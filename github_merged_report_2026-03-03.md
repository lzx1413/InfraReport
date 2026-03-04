# GitHub Stars 合并报告 - 2026-03-03

**合并日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库数量**: 11

## 目录

1. [ByteDance-Seed/VeOmni](#ByteDance-Seed-VeOmni)
2. [ModelTC/LightX2V](#ModelTC-LightX2V)
3. [flashinfer-ai/flashinfer](#flashinfer-ai-flashinfer)
4. [hao-ai-lab/FastVideo](#hao-ai-lab-FastVideo)
5. [huggingface/diffusers](#huggingface-diffusers)
6. [modelscope/DiffSynth-Engine](#modelscope-DiffSynth-Engine)
7. [modelscope/DiffSynth-Studio](#modelscope-DiffSynth-Studio)
8. [sgl-project/sglang](#sgl-project-sglang)
9. [vipshop/cache-dit](#vipshop-cache-dit)
10. [vllm-project/vllm-omni](#vllm-project-vllm-omni)
11. [vllm-project/vllm](#vllm-project-vllm)

---

<a id="ByteDance-Seed-VeOmni"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1688
- **最后更新**: 2026-03-04T11:15:18Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yifan Pi

## AI分析总结

根据提供的仓库README摘要和提交记录，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：为 `transformers-v5` 添加了 Qwen3.5（密集）模型的支持，目前是文本输入训练支持的第一步（Step 1/N）。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：在 `model` 模块中引入了对 Qwen3.5 密集模型的支持，专注于文本输入训练。
- **与项目方向的关系**：VeOmni 旨在通过模型中心的分布式配方库扩展任意模态模型的训练。此次更新直接扩展了支持的模型架构（特别是大语言模型），符合项目“Scaling Any Modality Model Training”的目标，增强了框架在文本模态上的覆盖范围。

### 3. 对项目的影响和潜在意义
- **直接影响**：用户现在可以在 VeOmni 框架中使用 Qwen3.5 进行文本训练，丰富了模型选择。
- **潜在意义**：作为 Step 1/N，这可能是后续支持多模态（如图像、音频）训练的基础。Qwen3.5 作为先进的开源大模型，其集成有助于提升框架的实用性和吸引力，可能吸引更多开发者使用。

### 4. 值得关注的技术点
- **模型集成**：如何将 Qwen3.5 适配到 `transformers-v5` 框架中，并确保分布式训练配方的兼容性。
- **分步实施**：更新注明是“Step1/N”，暗示后续可能扩展至多模态输入或推理优化，值得跟踪进展。

### 5. 基于项目背景的提交影响分析
- VeOmni 的核心是提供分布式训练配方库以简化大规模多模态模型训练。此次提交：
  - **强化模型生态**：通过添加主流大模型（Qwen3.5），增强了框架的覆盖面和实用性。
  - **渐进式扩展**：从文本输入开始，可能为后续支持更复杂的多模态场景（如视觉-语言模型）铺路，符合项目“Any Modality”的愿景。
  - **社区与协作**：集成热门开源模型有助于吸引社区贡献，推动配方库的丰富和优化。

**总结**：昨日更新是 VeOmni 框架在模型支持上的重要扩展，以功能新增为主，通过集成 Qwen3.5 模型强化了文本训练能力，并为未来多模态支持奠定基础，直接支持了项目扩展任意模态模型训练的核心目标。

## 详细提交记录

### [c1f5d73](https://github.com/ByteDance-Seed/VeOmni/commit/c1f5d73795678d0f8cd3004f856dcabd88263357)

- **作者**: Yifan Pi
- **时间**: 2026-03-03T22:45:57Z
- **提交信息**: [model] feat: [transformers-v5] Add qwen3_5 (dense) support Step1/N: text input training support (#523)



---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2014
- **最后更新**: 2026-03-04T09:24:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5075
- **最后更新**: 2026-03-04T07:59:17Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Chauncey, Brian K. Ryu, amitz-nv

## AI分析总结

根据提供的提交记录和README摘要（FlashInfer是一个专注于高性能Transformer推理加速的库），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了Python进程关闭时因导入系统已卸载而导致的`ImportError`。
- **功能新增**：为基准测试工具添加了FP8输入/BF16输出的支持；为自动调优器增加了CUDA图和冷L2缓存支持。
- **性能优化**：更新了`trtllm-gen`的批处理GEMM内核，提升了速度并扩展了支持的数据类型和激活函数。
- **文档更新**：更新了README以反映新的`--out_dtype`参数。
- **维护/配置**：添加了代码所有者配置文件。

### 2. 关键变更点及其与项目整体方向的关系
- **修复vLLM集成关闭错误** (`2371ee8`)：直接解决了FlashInfer作为vLLM等大型推理框架底层依赖时的**稳定性**问题，增强了在生产环境中的健壮性。
- **扩展FP8支持与基准测试** (`e08e8f3`)：新增了对`fp8_e4m3`/`fp8_e5m2`输入和`bfloat16`输出的支持。这直接服务于项目的核心目标——**支持最新硬件（如H100/ Blackwell）的高效低精度计算**，并提供了量化工作流的性能验证工具。
- **增强自动调优器** (`9b223bb`)：引入CUDA图和冷缓存分析能力。这提升了**内核选择的最优性**，使自动调优能更好地模拟实际推理场景（尤其是首次运行），从而提升最终性能。
- **更新GEMM内核** (`4f422f5`)：通过提供更快、支持更多数据类型（NVFP4、MXFP8+Relu²）的内核，直接**提升核心计算操作的性能**，这是推理加速库的根本。

### 3. 对项目的影响和潜在意义
- **提升集成体验与可靠性**：修复vLLM关闭错误，降低了用户（尤其是vLLM用户）遇到无害但令人困惑的警告的几率，提升了专业形象。
- **拥抱下一代数据格式**：对FP8的全面支持（输入、输出、基准测试）使FlashInfer保持在**低精度推理前沿**，有助于用户评估和部署量化模型。
- **优化性能与适应性**：自动调优和GEMM内核的更新意味着FlashInfer生成的代码在更多硬件和模型配置下能达到**更高的峰值性能**。
- **促进社区协作**：添加代码所有者配置有助于**规范化大型项目的维护流程**。

### 4. 值得关注的技术点
- **Python析构与模块卸载的时序问题**：修复方案展示了处理Python关闭时资源清理的常见陷阱。
- **FP8量化工作流的完整实现**：包括正确的每张量缩放、尺度融合，以及混合精度（FP8输入，BF16输出）支持，体现了对量化细节的深入处理。
- **生产级自动调优**：支持CUDA图（减少启动开销）和冷L2缓存（模拟真实负载）分析，使调优结果更贴近实际部署环境。
- **专用GEMM内核演进**：针对特定数据类型（如NVFP4）和激活函数（如MXFP8 with Relu²）优化内核，显示了面向特定硬件和模型架构的深度优化。

### 5. 基于项目背景的提交影响分析
FlashInfer的目标是成为**最快、最通用的Transformer推理加速库**。昨日的更新从多个维度推动项目向该目标发展：
- **巩固核心价值（速度与通用性）**：GEMM内核更新和自动调优增强直接提升了**速度**；扩展的FP8和数据类型支持增强了应对不同模型格式的**通用性**。
- **强化生产就绪度**：修复vLLM集成错误和增强自动调优的现实模拟，都使FlashInfer更**稳定、可靠**，更适合集成到像vLLM这样的生产系统中。
- **保持技术领先性**：积极集成对FP8等新数据格式的支持，确保库能充分利用**最新GPU硬件**的计算能力，维持其技术竞争力。
- **完善开发者生态**：通过更新文档和内部维护配置，改善了开发者体验，有助于项目的**长期健康维护**。

**总结**：昨日的更新是一次均衡的推进，既解决了紧迫的集成稳定性问题，又在核心的性能、前沿格式支持和工具链成熟度上做出了实质性改进，整体上巩固了FlashInfer作为高性能推理底层库的地位。

## 详细提交记录

### [2371ee8](https://github.com/flashinfer-ai/flashinfer/commit/2371ee8687f69b1f6880f482d6f591fc6932a47d)

- **作者**: Chauncey
- **时间**: 2026-03-03T19:53:58Z
- **提交信息**: fix: ImportError in AllReduceFusionWorkspace destructor during Python shutdown (#2659)

<!-- .github/pull_request_template.md -->

## 📌 Description
 vLLM has integrated the latest flashinfer.

However, when vLLM shuts down, flashinfer throws the following error:
```
(Worker pid=2113423) (Worker_TP2 pid=2113423) Exception ignored in: <function AllReduceFusionWorkspace.__del__ at 0x7ff5d5ffd940>
(Worker pid=2113423) (Worker_TP2 pid=2113423) Traceback (most recent call last):
(Worker pid=2113423) (Worker_TP2 pid=2113423)   File "/mnt/data4/jxy/venv/lib/python3.12/site-packages/flashinfer/comm/workspace_base.py", line 72, in __del__
(Worker pid=2113423) (Worker_TP2 pid=2113423) ImportError: sys.meta_path is None, Python is likely shutting down
(Worker pid=2113421) (Worker_TP0 pid=2113421) Exception ignored in: <function AllReduceFusionWorkspace.__del__ at 0x7f0d30f2d940>
(Worker pid=2113421) (Worker_TP0 pid=2113421) Traceback (most recent call last):
(Worker pid=2113421) (Worker_TP0 pid=2113421)   File "/mnt/data4/jxy/venv/lib/python3.12/site-packages/flashinfer/comm/workspace_base.py", line 72, in __del__
(Worker pid=2113421) (Worker_TP0 pid=2113421) ImportError: sys.meta_path is None, Python is likely shutting down
(Worker pid=2113424) (Worker_TP3 pid=2113424) Exception ignored in: <function AllReduceFusionWorkspace.__del__ at 0x7f8630109940>
(Worker pid=2113424) (Worker_TP3 pid=2113424) Traceback (most recent call last):
(Worker pid=2113424) (Worker_TP3 pid=2113424)   File "/mnt/data4/jxy/venv/lib/python3.12/site-packages/flashinfer/comm/workspace_base.py", line 72, in __del__
(Worker pid=2113424) (Worker_TP3 pid=2113424) ImportError: sys.meta_path is None, Python is likely shutting down
(Worker pid=2113422) (Worker_TP1 pid=2113422) Exception ignored in: <function AllReduceFusionWorkspace.__del__ at 0x7f9179e09940>
(Worker pid=2113422) (Worker_TP1 pid=2113422) Traceback (most recent call last):
(Worker pid=2113422) (Worker_TP1 pid=2113422)   File "/mnt/data4/jxy/venv/lib/python3.12/site-packages/flashinfer/comm/workspace_base.py", line 72, in __del__
(Worker pid=2113422) (Worker_TP1 pid=2113422) ImportError: sys.meta_path is None, Python is likely shutting down

```
 






It can be observed that the vLLM Python process is exiting, and
`__del__` is being triggered. At that point, the import system has
already been torn down, so `warnings` can no longer be imported.
 
 
 
 
<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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

* **Chores**
  * Internal code organization and cleanup with no user-facing changes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [e08e8f3](https://github.com/flashinfer-ai/flashinfer/commit/e08e8f3632fb155438803f208258c38e2e46e8df)

- **作者**: Brian K. Ryu
- **时间**: 2026-03-03T18:15:16Z
- **提交信息**: benchmarks: Add FP8 input / BF16 output in ragged prefill benchmark (#2666)

<!-- .github/pull_request_template.md -->

## 📌 Description

* Add `--out_dtype` support to
`testBatchPrefillWithRaggedKVCacheWrapper` to enable FP8 input with BF16
output, specifically enabling `trtllm-native`
(`trtllm_ragged_attention_deepseek`) with `Q/K/V = fp8_e4m3` and `O =
bfloat16`.
* Fix Q tensor FP8 quantization to use proper per-tensor scaling
(matching K/V behavior) instead of a bare `.to()` cast, and fold
dequantization scales into `bmm1_scale/bmm2_scale` for the
`trtllm-native` backend.
* Update `README` to document the new `--out_dtype` attention flag and
correct outdated `--q_dtype/--kv_dtype` descriptions.

Example:
```
$ python3 flashinfer_benchmark.py --routine BatchPrefillWithRaggedKVCacheWrapper --backends trtllm-native --batch_size 8 --s_qo 8192 --s_kv 8192 --num_qo_heads 128 --num_kv_heads 128 --head_dim_qk 192 --head_dim_vo 128 --q_dtype fp8_e4m3 --kv_dtype fp8_e4m3 --out_dtype bfloat16 -v
[INFO] args = Namespace(routine='BatchPrefillWithRaggedKVCacheWrapper', no_cuda_graph=False, use_cupti=False, use_cuda_events=False, refcheck=False, allow_output_mismatch=False, random_seed=42, verbose=1, output_path=None, num_iters=30, dry_run_iters=5, case_tag=None, generate_repro_command=False, repro_command='', backends=['trtllm-native'], page_size=0, batch_size=8, s_qo=8192, s_kv=8192, num_qo_heads=128, num_kv_heads=128, head_dim_qk=192, head_dim_vo=128, head_dim_ckv=None, head_dim_kpe=None, q_dtype='fp8_e4m3', kv_dtype='fp8_e4m3', out_dtype='bfloat16', causal=False, random_actual_seq_len=False)
[INFO] Running testBatchPrefillWithRaggedKVCacheWrapper
[INFO] FlashInfer version: 0.6.4
[VERBOSE] Average actual qo seq len: 8192
[VERBOSE] Average actual kv seq len: 8192
[PERF] trtllm-native  :: median time 21.833 ms; std 0.424 ms; achieved tflops 2014.435 TFLOPs/sec; achieved tb_per_sec 0.295 TB/sec
```

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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
  * Extended q/kv tensor support to include fp8_e4m3 and fp8_e5m2
* Added an out_dtype option to control output data type (defaults to
q_dtype); enables FP8→other output variants

* **Documentation**
* Updated descriptions and help text to reflect expanded dtype options
and out_dtype semantics

* **Other**
* Runtime validation and warnings for dtype interactions; results now
log the chosen out_dtype for clarity
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9b223bb](https://github.com/flashinfer-ai/flashinfer/commit/9b223bb98900a94334675b123d6518af82bd8cba)

- **作者**: amitz-nv
- **时间**: 2026-03-03T16:54:55Z
- **提交信息**: feat: Autotuner support CUDA graph and cold L2 cache (#2663)

## 📌 Description

Adds support for CUDA graph and cold L2 cache in the autotuner.
Mostly copied from TRTLLM, see
https://github.com/NVIDIA/TensorRT-LLM/blob/63c33c7c9a705e6d194a53b7ed54bbaa11494f7d/tensorrt_llm/_torch/autotuner.py#L1134

Currently:
* Both are disabled by default
* Both are enabled specifically in `trtllm_fp4_block_scale_moe_op`

## 🔍 Related Issues

Not aware of any.

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added CUDA graph profiling and batched replay option to speed and
stabilize kernel profiling.
* Added cold L2-cache profiling mode to support cold-cache tuning
scenarios.
* Improved CUDA error diagnostics and automatic L2 cache-size detection
for clearer runtime reporting.

* **Chores**
* Tuning configuration now propagates new flags through the autotuning
flow and refining helpers.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: amitz-nv <203509407+amitz-nv@users.noreply.github.com>

### [140ba64](https://github.com/flashinfer-ai/flashinfer/commit/140ba64bb9743a42c248f6bf7ace09f7ad5bf07f)

- **作者**: Alex Yang
- **时间**: 2026-03-03T15:25:04Z
- **提交信息**: Add code owner for scripts/codeowner_overrides.json (#2656)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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

* **Chores**
  * Added an internal configuration entry for code ownership overrides.
* Internal-only adjustment; no changes to UI, user workflows, or runtime
behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: coderabbitai[bot] <136622811+coderabbitai[bot]@users.noreply.github.com>

### [4f422f5](https://github.com/flashinfer-ai/flashinfer/commit/4f422f5b4783d73041d9dda8fecc6a17c9d21603)

- **作者**: amitz-nv
- **时间**: 2026-03-03T09:18:05Z
- **提交信息**: perf: Update trtllm-gen batched GEMM kernels - faster, more NVFP4 tile dims, MXFP8 with relu2 act (#2667)

## 📌 Description

Updates the trtllm-gen batched GEMM kernel hashes and
`include/flashinfer/trtllm/batched_gemm/trtllmGen_bmm_export` directory
for:
* Faster batched GEMM kernels
* Additional NVFP4 tile dims kernels
* Additional MXFP8 with Relu^2 non-gated activation kernels

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

* **Chores**
* Updated an internal batched matrix‑multiplication interface (call
signature changed).
* Refreshed native artifact references and checksums for GPU-accelerated
components.
* No end-user behavioral changes expected; these are internal
compatibility and maintenance updates.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: amitz-nv <203509407+amitz-nv@users.noreply.github.com>
Co-authored-by: jimmzhou <jimmzhou@nvidia.com>
Co-authored-by: Jimmy Zhou <79552142+jimmyzho@users.noreply.github.com>
Co-authored-by: Alex Yang <aleozlx@gmail.com>
Co-authored-by: Zihao Ye <zihaoye.cs@gmail.com>



---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3121
- **最后更新**: 2026-03-04T07:09:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 32915
- **最后更新**: 2026-03-04T11:59:11Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: YiYi Xu

## AI分析总结

根据提供的提交记录和README摘要，以下是针对 `huggingface/diffusers` 仓库昨日更新的分析总结：

### 1. **主要更新类型**
- **功能新增与Bug修复**：本次提交主要涉及模块化（modular）功能中 `trust_remote_code` 参数的传递逻辑调整，并增加了相关测试用例，属于功能优化与潜在Bug修复的结合。

### 2. **关键变更点及其与项目整体方向的关系**
- **变更点**：在模块化组件中，不再将 `trust_remote_code` 参数传递给外部仓库（external repos），并更新了警告信息和测试逻辑。
- **与项目方向的关系**：`diffusers` 项目致力于提供可扩展、安全的扩散模型工具库。此变更强化了代码安全性，避免因远程代码信任问题引入风险，符合项目对模块化、安全可控设计的追求。

### 3. **对项目的影响和潜在意义**
- **安全性提升**：减少因自动传递 `trust_remote_code` 可能导致的安全隐患，增强用户对第三方代码的主动控制。
- **开发者体验**：通过更新警告和测试，帮助开发者更清晰地理解参数传递行为，降低误用风险。
- **模块化维护**：为自定义模型组件（如 `update_component`）提供更稳定的支持，促进生态扩展。

### 4. **值得关注的技术点**
- **参数传递优化**：针对外部仓库的 `trust_remote_code` 处理逻辑调整，体现了对依赖安全性的重视。
- **测试覆盖增强**：新增多项测试，确保自定义模型场景下的兼容性与可靠性。
- **协作开发痕迹**：提交中融合了社区贡献者（@DN6）的建议，反映项目活跃的协作生态。

### 5. **基于项目背景的提交影响分析**
- **背景关联**：README 强调项目专注于扩散模型的易用性与可扩展性，支持模块化管道和自定义组件。
- **发展影响**：此次提交通过细化参数管理，进一步巩固了模块化架构的安全性基础，有助于吸引企业级用户和注重安全的开发者，同时为未来集成更多第三方模型铺平道路，推动项目向更稳健、可信的生态演进。

---
**总结**：本次更新虽看似细微，但通过安全参数优化和测试强化，提升了 `diffusers` 在模块化场景下的安全性与可靠性，符合项目长期追求的可扩展、安全可控的核心目标。

## 详细提交记录

### [1fe688a](https://github.com/huggingface/diffusers/commit/1fe688a651bc078326082b8927f8fbdd6cefeef0)

- **作者**: YiYi Xu
- **时间**: 2026-03-03T12:36:36Z
- **提交信息**: [modular] not pass trust_remote_code to external repos  (#13204)

* add

* update warn

* add a test

* updaqte

* update_component with custom model

* add more tests

* Apply suggestion from @DN6

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

* up

---------

Co-authored-by: yiyi@huggingface.co <yiyi@ip-26-0-161-123.ec2.internal>
Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>



---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 378
- **最后更新**: 2026-03-02T11:35:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 11899
- **最后更新**: 2026-03-04T09:38:11Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

根据提供的提交记录和README摘要，以下是对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：引入了 `qwen_image layercontrol v2`，推测为针对图像生成或编辑的图层控制功能进行了重大版本升级。

### 2. 关键变更点及其与项目整体方向的关系
- **图层控制功能升级**：提交 `c5aaa1d` 合并了 `layercontrol_v2` 分支，表明项目在图像合成或编辑的图层管理方面进行了功能增强或重构。
- **与项目方向的关系**：DiffSynth-Studio 作为一个图像生成/编辑工具（从README中的logo和名称推断），图层控制是核心功能之一。此次更新直接强化了用户在合成过程中的精细控制能力，符合项目向更专业、可定制化方向发展的目标。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：V2版本可能带来更直观、强大的图层操作界面或API，提高创作效率。
- **技术债务管理**：版本升级可能涉及代码重构，为后续功能扩展奠定基础。
- **社区贡献整合**：通过Pull Request（#1306）合并，显示项目积极接纳社区改进，促进生态活跃度。

### 4. 值得关注的技术点
- **Qwen-Image集成**：`qwen_image` 可能指代集成的大型视觉模型（如阿里云的Qwen-VL），结合图层控制，可能实现了基于AI的智能图层编辑或生成功能。
- **版本化重构**：`layercontrol_v2` 暗示对原有图层控制系统进行了较大幅度重构，可能涉及架构优化或性能改进。

### 5. 基于项目背景的提交影响分析
- **强化核心功能**：README中项目定位为图像合成/编辑工具，图层控制是此类工具的关键模块。此次更新直接提升了核心功能的竞争力，有助于吸引专业用户。
- **技术生态扩展**：若集成Qwen等AI模型，表明项目正探索“AI驱动+精细化控制”的混合工作流，这与当前AIGC工具向可控性、可编辑性发展的趋势一致。
- **协作开发模式**：通过分支合并和PR流程，项目保持了规范的开发管理，有利于长期维护和社区参与。

---
**总结**：昨日更新聚焦于图层控制功能的版本升级，通过重构或增强该模块，进一步巩固了项目作为专业图像合成工具的核心能力，并可能融合AI模型提升智能化水平，符合AIGC领域向可控化、精细化发展的行业趋势。

## 详细提交记录

### [c5aaa1d](https://github.com/modelscope/DiffSynth-Studio/commit/c5aaa1da418f17b74c42da6cc973af73dab94e7f)

- **作者**: Zhongjie Duan
- **时间**: 2026-03-03T13:06:25Z
- **提交信息**: Merge pull request #1306 from mi804/layercontrol_v2

qwen_image layercontrol v2

### [6bcb99f](https://github.com/modelscope/DiffSynth-Studio/commit/6bcb99fd2ee88610bdd882702f64cf4299268d28)

- **作者**: Zhongjie Duan
- **时间**: 2026-03-03T13:04:04Z
- **提交信息**: Merge branch 'main' into layercontrol_v2



---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24067
- **最后更新**: 2026-03-04T11:27:42Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 28
- **主要提交者**: Eric Zhang, Liangsheng Yin, Jiayi Yan

## AI分析总结

根据提供的提交记录和README摘要（SGLang项目是一个用于大语言模型推理的框架），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：修复了多个关键问题，包括CI流程、内核拓扑解析、边界验证、JSON解析、端口冲突检测等。
- **功能新增**：新增了对新硬件（如H200/B200、AMD NPU）和新模型（如Qwen 3 Next、Kimi K2.5、DeepSeek-V3.2）的支持，以及专家并行、权重加载日志、HTTP端口预留等功能。
- **性能优化**：针对特定硬件（如SM90/SM120启用XQA、Hopper架构的GDN支持）和模型配置进行了性能调优。
- **CI/工具链改进**：更新了CI工作流、基准测试脚本和CLI工具。
- **文档更新**：增加了GDN注意力后端矩阵的文档。

### 2. 关键变更点及其与项目整体方向的关系
- **硬件与模型生态扩展**：提交中大量涉及对新硬件（NVIDIA H200/B200、AMD NPU）和新模型（Qwen、Kimi、DeepSeek）的适配与优化，这与SGLang作为高效推理框架的目标一致，旨在扩大其支持的硬件和模型范围，提升通用性。
- **推理性能与稳定性**：多项修复和优化（如作业队列并发提升、KVCache传输、调度流默认设置）直接针对生产环境下的推理性能和稳定性，强化了其作为生产级服务的可靠性。
- **开发者体验与运维**：CI流程修复、CLI改进、端口冲突提前检测、更丰富的日志和错误处理，这些变更降低了使用和运维门槛，改善了开发者体验。

### 3. 对项目的影响和潜在意义
- **提升生产就绪度**：通过修复可能导致服务器崩溃/挂起（如重复请求ID）、数据损坏（如JSON解析）的严重Bug，并增强系统健壮性（如边界验证），显著提升了系统的稳定性和安全性。
- **加速模型部署**：对新模型和硬件的快速支持，使用户能更快地在SGLang上部署最新的LLM，保持了项目的技术前沿性。
- **优化资源利用率**：性能调优和并发控制（如`max_concurrent_jobs`）的改进，有助于提高硬件利用率和吞吐量，降低推理成本。
- **增强可维护性**：CI/CD流程的完善和文档的补充，有利于项目的长期可持续开发和团队协作。

### 4. 值得关注的技术点
- **专家并行（Expert Parallelism）**：在SRT Runner中新增支持，这是面向MoE（混合专家）模型的重要分布式推理技术。
- **FlashInfer与GDN集成**：为Hopper架构添加K-last SSM布局支持，可能涉及新一代注意力机制的优化。
- **XQA启用**：在SM90和SM120架构上启用，可能是一种新的注意力加速技术。
- **工具调用流式化**：DeepSeek-V3.2的函数调用参数以JSON格式流式传输，改善了交互体验。
- **Triton内核版本锁定**：针对特定模型和硬件（如Qwen 3 Next on H200/B200）使用调优后的Triton 3.5.1，体现了对性能细节的深度优化。

### 5. 基于项目背景的提交影响分析
SGLang旨在提供**高性能、低延迟、易用**的LLM服务框架。昨日的提交集体指向这一目标的深化：
- **性能与延迟**：通过硬件特定优化（XQA、Triton调参、FlashInfer支持）和调度策略调整，直接提升推理速度。
- **易用性与可扩展性**：简化部署（新模型支持）、改善运维（CI/日志/CLI）、增强API（Score API返回token用量、OpenAI API兼容的基准测试），降低了用户的使用难度。
- **生态构建**：积极适配最新的硬件和模型，巩固了其作为主流推理框架之一的地位，吸引更广泛的开发者和企业用户。
- **工业级稳健性**：对生产环境中可能出现的各种边界情况和故障（端口冲突、重复请求、错误数据）进行预防和处理，体现了向企业级服务迈进的成熟度。

**总结**：昨日的更新是一次全面的迭代，核心是**强化稳定性、扩展兼容性、优化性能**，使SGLang在快速发展的LLM推理生态中保持竞争力和实用性。

## 详细提交记录

### [e6411ba](https://github.com/sgl-project/sglang/commit/e6411ba315e0ea8006fb2c6ebf33c8170edc62a1)

- **作者**: Eric Zhang
- **时间**: 2026-03-03T23:54:51Z
- **提交信息**: Increase max_concurrent_jobs in job queue (#19797)

### [c7ffbf2](https://github.com/sgl-project/sglang/commit/c7ffbf25e940018326c24a389047b8fc45d6dcf1)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-03T23:17:16Z
- **提交信息**: [CI] Fix `rerun-ut` workflow: add DeepEP install, RDMA env, Blackwell detection (#19803)

### [753da27](https://github.com/sgl-project/sglang/commit/753da275358e4b4c9abcdfefae24dd192e5029b9)

- **作者**: Jiayi Yan
- **时间**: 2026-03-03T23:15:36Z
- **提交信息**: [Bugfix] fix parse_lscpu_topology bug (#18520)

### [069c7e4](https://github.com/sgl-project/sglang/commit/069c7e4188aca6ef69c0b81dfa05abba49685946)

- **作者**: Cao E
- **时间**: 2026-03-03T23:04:44Z
- **提交信息**: Fix CI failures (#19303)

### [b8c71f8](https://github.com/sgl-project/sglang/commit/b8c71f895e978bcbf9962324cf34e36f0f6fcbbc)

- **作者**: Yi Zhong
- **时间**: 2026-03-03T22:47:19Z
- **提交信息**:  Add tuned triton==3.5.1 h200 tp2, tp4 for qwen 3 next (#15948)

Signed-off-by: vincentzed

### [0c760c4](https://github.com/sgl-project/sglang/commit/0c760c4cd73b2dd60c9c04fc458833bfe1c18011)

- **作者**: Yi Zhong
- **时间**: 2026-03-03T22:47:05Z
- **提交信息**: Add tuned triton==3.5.1 b200 tp2, tp4 for qwen 3 next (#15917)

Signed-off-by: vincentzed <207368749+vincentzed@users.noreply.github.com>

### [fb37c0a](https://github.com/sgl-project/sglang/commit/fb37c0a400702a4b4645e5a8addd65d1a3ef28fb)

- **作者**: Jonah Bernard
- **时间**: 2026-03-03T22:16:35Z
- **提交信息**: [args] Add Expert Parallelism Argument To SRT Runner (#18492)

Co-authored-by: Qiaolin Yu <liin1211@outlook.com>

### [f7897de](https://github.com/sgl-project/sglang/commit/f7897def960b721e4472895c445b7182d844fb4b)

- **作者**: Praneth Paruchuri
- **时间**: 2026-03-03T22:16:13Z
- **提交信息**: [Feature] Improve weight loading log  (#18651)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [9305f0e](https://github.com/sgl-project/sglang/commit/9305f0e58dca327bbb3dbd7622405e64d31d4449)

- **作者**: Brayden Zhong
- **时间**: 2026-03-03T22:14:01Z
- **提交信息**: Support `triton_kernels` for GPT-OSS on SM120 (#19718)

Co-authored-by: amittell 1388680+amittell@users.noreply.github.com

### [1135e21](https://github.com/sgl-project/sglang/commit/1135e214b362465d0af3813f1e290ecb84e24ccf)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-03T22:10:49Z
- **提交信息**: [CI] support `/rerun-ut` command in slash handler (#19800)

### [5b2e275](https://github.com/sgl-project/sglang/commit/5b2e2750b555182a29e718a42464be43bd4ec551)

- **作者**: Sam (Kesen Li)
- **时间**: 2026-03-03T22:09:44Z
- **提交信息**: Enable XQA for SM90 and SM120 (#17115)

Co-authored-by: Xiaowei Wang <100599594+xiaoweiw-nv@users.noreply.github.com>

### [dc92f88](https://github.com/sgl-project/sglang/commit/dc92f88a21716eeee9022ebdbc14172ddd92c0d3)

- **作者**: Kangyan-Zhou
- **时间**: 2026-03-03T21:48:04Z
- **提交信息**: Enhance bench_multiturn.py with OpenAI API support and richer metrics (#19724)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [f749802](https://github.com/sgl-project/sglang/commit/f7498024021d8b13dda70de55e7d35d617eae26f)

- **作者**: Guy Stone
- **时间**: 2026-03-03T21:45:35Z
- **提交信息**: [Score API][18132] return token usage in Score API response (#18381)

### [b0f2669](https://github.com/sgl-project/sglang/commit/b0f26698f528e43136fe320e594a7c73947ec734)

- **作者**: almaslof
- **时间**: 2026-03-03T21:44:38Z
- **提交信息**: feat(benchmark script): add similar to vllm --ready-check-timeout-sec parameter (#15466)

### [ac2819c](https://github.com/sgl-project/sglang/commit/ac2819c81fcd15ac272dba8873784be21f34da46)

- **作者**: Rahul Vijayaraghavan
- **时间**: 2026-03-03T21:43:58Z
- **提交信息**: Fix assertion tolerance for bf16 precision in triton attention UT (#17461)

Signed-off-by: Rahul Vijayaraghavan <rahul.vijayaraghavan@intel.com>

### [85ab6a7](https://github.com/sgl-project/sglang/commit/85ab6a7f549e34b0dfb8d897b615a3e5dc882a4c)

- **作者**: Karthik Koralla
- **时间**: 2026-03-03T21:03:49Z
- **提交信息**: cli: Add lazy imports and fail-fast config validation (RFC #9853) (#19368)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [d6ac5f2](https://github.com/sgl-project/sglang/commit/d6ac5f23cc27c0f24d4a1cc5464f841d370c4aa9)

- **作者**: zwang86
- **时间**: 2026-03-03T21:00:34Z
- **提交信息**: [Docs] Add GDN attention backends matrix documentation (#19755)

Co-authored-by: Zeyu Wang <zeyu.wang@yahooinc.com>

### [cedb86a](https://github.com/sgl-project/sglang/commit/cedb86a950e32af1b22b670213776ccfe15e54b6)

- **作者**: xrwang8
- **时间**: 2026-03-03T19:59:18Z
- **提交信息**: Feature:Reserve HTTP server port before model loading to immediately detect port  conflicts instead of failing after several minutes of model loading. (#17754)

Signed-off-by: xrwang8 <xrwang8@gmail.com>

### [2e1b9e2](https://github.com/sgl-project/sglang/commit/2e1b9e254734171e9d29767aca4168ef7c77a3c2)

- **作者**: doujiang24
- **时间**: 2026-03-03T19:55:15Z
- **提交信息**: Fix routed_dp_rank boundary validation (#19762)

Signed-off-by: doujiang24 <doujiang24@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [05f68e1](https://github.com/sgl-project/sglang/commit/05f68e12300b993e2738f720a5d98d4d4dc342d3)

- **作者**: Hubert Lu
- **时间**: 2026-03-03T19:42:48Z
- **提交信息**: [AMD] Fix the hipDeviceGetName issue in ROCm based docker images (#19440)

Co-authored-by: bingxche <Bingxu.Chen@amd.com>

### [85f7a0a](https://github.com/sgl-project/sglang/commit/85f7a0aa3077e9bdec83ca9eb7f3687d3d51050b)

- **作者**: yefei12
- **时间**: 2026-03-03T18:41:15Z
- **提交信息**: feat: support Kimi K2.5 for Eagle3 (#19689)

Co-authored-by: chenyefei.cyf <chenyefei.cyf@U-9V5T77LW-2356.local>
Co-authored-by: GeLee-Q <865038696@qq.com>
Co-authored-by: Gao016 <yngao016@163.com>
Co-authored-by: sxl1993 <1218197792@qq.com>

### [95e4a25](https://github.com/sgl-project/sglang/commit/95e4a25b17c36434206c8ff4871c6985f3714b7d)

- **作者**: SoluMilken
- **时间**: 2026-03-03T16:57:02Z
- **提交信息**: [fix typo]: funtion -> function (1 line change) (#19790)

### [daabfe7](https://github.com/sgl-project/sglang/commit/daabfe7e4c76a0d9b12b5e90f062addf7c4d5c35)

- **作者**: Tamir Baydasov
- **时间**: 2026-03-03T13:50:37Z
- **提交信息**: [hotfix] fix apply function name compressed_tensors_w4a4_mxint4_moe (#19713)

### [c6377bb](https://github.com/sgl-project/sglang/commit/c6377bbbca276c0e8f63d0d978c69ceb095aa10a)

- **作者**: xutizhou
- **时间**: 2026-03-03T12:30:48Z
- **提交信息**: feat(gdn): add FlashInfer K-last SSM layout support for GDN prefill and decode for Hopper (#18361)

Co-authored-by: HongliMi <106042350+HongliMi@users.noreply.github.com>
Co-authored-by: xiaozhoupy <181108106+zhou9402@users.noreply.github.com>
Co-authored-by: Jinyan Chen <93358689+liz-badada@users.noreply.github.com>
Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>
Co-authored-by: eigen <52445717+yyihuang@users.noreply.github.com>

### [d939e26](https://github.com/sgl-project/sglang/commit/d939e26585ac8b319793895823daddd28863d6b1)

- **作者**: Jasonzhang517
- **时间**: 2026-03-03T11:38:15Z
- **提交信息**: [model gateway][0/N] router EPD support: add encoder grpc server backend support (#16552)

Co-authored-by: Zongyao Chen <ZongYao.Chen@linux.alibaba.com>
Co-authored-by: Zongyao Chen <solar1s@163.com>

### [facde4c](https://github.com/sgl-project/sglang/commit/facde4c6d3f3b820c00f053fe9a45c9a086deaf2)

- **作者**: Shangming Cai
- **时间**: 2026-03-03T11:35:21Z
- **提交信息**: [PD] Enable all CP ranks for KVCache transfer  (#19765)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [365ca1e](https://github.com/sgl-project/sglang/commit/365ca1edb5af06de8d76fd85fa882df2b0ad1654)

- **作者**: shengzhaotian
- **时间**: 2026-03-03T09:59:25Z
- **提交信息**: [NPU] bugs fix: fix a condition bug when using speculative inference on Qwen3 and Qwen3 moe  (#19532)

### [666caaf](https://github.com/sgl-project/sglang/commit/666caaf9ce76ea157ac546a80d2c9c901c5c926c)

- **作者**: Muqi Li
- **时间**: 2026-03-03T09:46:29Z
- **提交信息**: [Tool Call] Stream DeepSeek-V3.2 function call parameters in JSON format. (#16091)

Co-authored-by: Huixxi <uestc.hugo@gmail.com>

### [4c95953](https://github.com/sgl-project/sglang/commit/4c95953b77335f42eae5d3b59a00279008a6e639)

- **作者**: Shaun Kotek
- **时间**: 2026-03-03T09:07:46Z
- **提交信息**: Fix/nemotron mtp quantaized (#19433)

### [af0d35b](https://github.com/sgl-project/sglang/commit/af0d35b224c0ff04436dbcd41c6d72f0111b2deb)

- **作者**: Charles Chen
- **时间**: 2026-03-03T08:33:25Z
- **提交信息**: Fix: Reject requests with a duplicate request ID which can cause server crash/hang (#19035)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [6af0448](https://github.com/sgl-project/sglang/commit/6af0448cc9bff5fbf13fe84b50276e399f620516)

- **作者**: Muqi Li
- **时间**: 2026-03-03T08:10:07Z
- **提交信息**: [Bugfix] Catch errors when DeepSeek-V3.2 generates malformed JSON (#18174)

### [7a2d3df](https://github.com/sgl-project/sglang/commit/7a2d3df96fa16874a8bc1501ca113be659ae37f1)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-03T08:05:27Z
- **提交信息**: Apply default stream to priority 0 in scheduling. (#16438)



---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: 🤗 A PyTorch-native and Flexible Inference Engine with Hybrid Cache Acceleration and Parallelism for DiTs.
- **语言**: Python
- **星标数**: 1060
- **最后更新**: 2026-03-04T03:51:24Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据提供的仓库README摘要和提交记录，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：添加了新的示例配置文件（hopper configs）。

### 2. 关键变更点及其与项目整体方向的关系
- **新增Hopper配置示例**：提交中多次添加了与“hopper”相关的配置文件。
- **与项目方向的关系**：cache-dit是一个专注于混合缓存加速和并行化的PyTorch原生推理引擎，用于DiTs（Diffusion Transformers）。新增配置示例表明项目正在扩展其支持的模型架构或应用场景（可能指特定模型如“Hopper”），这符合项目作为灵活推理引擎的定位，旨在提供更多开箱即用的配置选项，降低用户使用门槛。

### 3. 对项目的影响和潜在意义
- **降低配置复杂度**：为用户提供了现成的配置文件，简化了特定模型（如Hopper）的部署和实验流程。
- **促进社区采用**：通过提供更多示例，有助于吸引用户尝试不同配置，加速项目在实际场景中的应用和测试。
- **潜在扩展性**：可能为未来支持更多模型变体或优化策略奠定基础，增强项目的通用性。

### 4. 值得关注的技术点
- **配置驱动的灵活性**：提交强调通过配置文件管理模型推理参数，体现了项目对可配置性和模块化设计的重视。
- **针对特定模型的优化**：“Hopper”可能指代某个DiT变体或应用场景，新增配置可能包含了针对该模型的缓存、并行化或硬件优化设置，值得进一步查看具体配置内容以了解技术细节。

### 5. 基于项目背景的提交影响分析
- **README背景回顾**：cache-dit旨在为🤗DiTs提供高效的混合缓存加速和并行化推理引擎，强调PyTorch原生和灵活性。
- **对项目发展的影响**：
  - **生态完善**：此次更新通过添加示例配置，丰富了项目的文档和示例资源，使用户能更快速地上手特定模型，符合项目“灵活”和“用户友好”的目标。
  - **加速迭代**：提供标准化配置可能促进社区贡献和反馈，帮助项目优化核心引擎的兼容性和性能。
  - **战略扩展**：如果“Hopper”代表新兴模型或应用，此举显示项目正紧跟DiT领域发展，及时集成新用例，保持技术前沿性。

**总结**：昨日更新主要为功能新增，通过添加Hopper示例配置文件，增强了项目的易用性和场景覆盖，符合其作为灵活推理引擎的发展方向，有助于推动社区采用和技术迭代。

## 详细提交记录

### [45012a7](https://github.com/vipshop/cache-dit/commit/45012a7ebaddc1740e018e7a9837ea92027a8cc5)

- **作者**: DefTruth
- **时间**: 2026-03-03T10:12:38Z
- **提交信息**: chore: add hopper example configs (#823)

* chore: add hopper configs

* chore: add hopper configs

* chore: add hopper configs

* chore: add hopper configs

* chore: add hopper configs

* chore: add hopper configs



---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 2912
- **最后更新**: 2026-03-04T12:09:29Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Yueqian Lin, Junhong Liu, Yuanheng Zhao

## AI分析总结

根据提供的README摘要（vLLM-Omni项目）和提交记录，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：提交1和提交3均为Bug修复，分别解决了Transformers 5.x兼容性问题以及模型子目录路径和GLM-Image生成问题。
- **功能增强/配置优化**：提交2允许通过YAML配置`chunk_size`和`left_context_size`参数，增强了异步分块处理的灵活性。

### 2. 关键变更点及其与项目整体方向的关系
- **Transformers兼容性修复**（提交1）：确保项目与最新版Transformers库（5.x）兼容，维持了vLLM-Omni作为**多后端推理引擎**的稳定性，支持HuggingFace等主流框架。
- **异步分块配置化**（提交2）：通过YAML配置分块参数，提升了**流式推理和长上下文处理**的灵活性，符合项目对高效、可配置推理的追求。
- **模型路径与多模态生成修复**（提交3）：解决了模型子目录路径解析和GLM-Image生成问题，强化了**多模态支持**（如图像生成）和复杂模型结构的兼容性。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：修复关键Bug减少了生产环境中的潜在故障，特别是对Transformers 5.x的支持避免了版本升级带来的中断。
- **可维护性增强**：配置化分块参数降低了代码硬编码依赖，便于用户根据硬件和场景调整性能。
- **多模态与扩展性**：路径修复和GLM-Image生成修复直接支持更复杂的模型部署，加强了项目在**视觉-语言模型**等领域的实用性。

### 4. 值得关注的技术点
- **Transformers 5.x适配**：可能涉及API变更或依赖更新，需关注后续版本兼容性策略。
- **YAML动态配置**：反映了项目向“配置驱动”架构发展，可能影响部署和自动化流程。
- **GLM-Image生成修复**：涉及多模态模型（如视觉生成）的推理流程，可能关联图像张量处理或跨模态调度优化。

### 5. 基于项目背景的提交影响分析
vLLM-Omni旨在成为**统一的高性能推理引擎**，支持多种硬件和模型类型。昨日更新：
- **强化核心定位**：通过Bug修复和配置优化，提升了在**多后端（如PyTorch、TensorRT）和多模态场景**下的可靠性，符合其“Omni”（全能）愿景。
- **促进生态整合**：Transformers兼容性修复确保了与HuggingFace生态的平滑对接，而GLM-Image修复则支持更广泛的模型家族（如GLM），扩展了应用场景。
- **优化用户体验**：YAML配置化降低了使用门槛，使流式处理等高级功能更易调整，有助于吸引更广泛的开发者群体。

---

**总结**：昨日更新以Bug修复和功能优化为主，重点提升了框架兼容性、配置灵活性和多模态支持，直接强化了vLLM-Omni作为统一推理引擎的核心能力，同时为复杂模型部署和用户自定义场景提供了更好支持。

## 详细提交记录

### [a3240fd](https://github.com/vllm-project/vllm-omni/commit/a3240fd484e3bd7ef150da56a948ae6ab7ab02bb)

- **作者**: Yueqian Lin
- **时间**: 2026-03-03T17:28:32Z
- **提交信息**: [Bugfix] Fix transformers 5.x compat issues in online TTS serving (#1536)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [742d845](https://github.com/vllm-project/vllm-omni/commit/742d845b8ea1c018cd5370a4b47e31bad407e6c3)

- **作者**: Junhong Liu
- **时间**: 2026-03-03T14:06:52Z
- **提交信息**: Make chunk_size and left_context_size configurable via YAML for async chunking (#1423)

Signed-off-by: Junhong Liu <98734602+LJH-LBJ@users.noreply.github.com>
Signed-off-by: Junhong Liu <ljh_lbj@163.com>

### [b13761e](https://github.com/vllm-project/vllm-omni/commit/b13761ed264e8160b622c1f1d0a0e62376efc2b2)

- **作者**: Yuanheng Zhao
- **时间**: 2026-03-03T10:40:53Z
- **提交信息**: [Bugfix] Fix filepath resolution for model with subdir and GLM-Image generation (#1609)

Signed-off-by: yuanheng <jonathan.zhaoyh@gmail.com>
Signed-off-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>



---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-04
**监控日期**: 2026-03-03
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 71889
- **最后更新**: 2026-03-04T12:09:32Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 17
- **主要提交者**: Nick Hill, zhrrr, Amr Mahdi

## AI分析总结

根据提供的提交记录和项目背景（vLLM 是一个高性能、易用的大语言模型推理和服务库），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及多个组件（模型运行器、ROCm、通信、音频处理等）。
- **功能新增/增强**：主要集中在**Model Runner V2**（支持分布式推理和推测解码）和**MoE（混合专家）模型**的优化。
- **性能优化**：包括非阻塞数据拷贝和新的性能基准测试。
- **CI/CD与构建**：涉及缓存认证、测试调整和基准测试添加。
- **测试覆盖与验证**：增加了新的测试用例和测试覆盖范围。
- **代码重构**：核心逻辑移动和内核创建。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **Model Runner V2 支持 DP & EP** (#35294) | 增强**分布式推理能力**，是vLLM作为**生产级服务库**支持大规模部署的关键。 |
| **修复 MM 模型 `inputs_embeds=None` 错误** (#35917) | 提升**多模态模型**的兼容性和稳定性，符合扩展模型支持的路线。 |
| **MoE 相关修复与优化** (#35813, #32564, #35870) | 针对**MoE模型**这一重要架构进行专项优化和问题修复，提升其推理效率与可靠性。 |
| **ROCm 平台多项修复** (#35887, #35601) | 加强对 **AMD GPU** 平台的支持和稳定性，体现其**硬件兼容性**的追求。 |
| **推测解码（Speculative Decoding）增强** (#35882, #34552) | 优化这一关键的**推理加速技术**，直接提升生成速度，是核心性能特性。 |
| **核心逻辑移动** (#35825) | 将 `save_tensorized_model` 移至 Worker，属于**代码结构优化**，可能为后续功能（如动态加载）做准备。 |
| **Intel Gaudi 3 性能基准** (#31025) | 扩展对**专用AI加速器**的评估和支持，拓宽硬件生态。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：大量Bug修复直接提高了核心功能（分布式推理、多模态、MoE、ROCm）的稳定性，减少生产环境风险。
- **性能与扩展性**：对推测解码、通信、MoE内核的优化，有望进一步提升**吞吐量和延迟**表现。分布式推理（DP/EP）的支持增强了水平扩展能力。
- **生态扩展**：持续加强对AMD ROCm和Intel Gaudi等**替代硬件平台**的支持与测试，降低用户部署的硬件依赖和成本。
- **开发者体验**：CI/CD的改进（如S3缓存认证）和测试覆盖率的增加，有助于维持项目开发效率和代码质量。

### 4. 值得关注的技术点
1.  **推测解码（Speculative Decoding）的深入优化**：提交 #34552 和 #35882 显示团队正在完善其在复杂场景（如稀疏MLA、多token）下的支持，这是前沿的推理加速技术。
2.  **Model Runner V2 的演进**：该组件显然是当前开发重点，旨在构建更强大、灵活的下一代模型执行引擎。
3.  **MoE模型的专项支持**：从内核创建（#32564）到参数修复（#35813），表明vLLM正在系统性地提升对MoE这类大型、高效模型架构的**原生支持**。
4.  **硬件后端的持续耕耘**：针对ROCm和Intel Gaudi的提交表明项目在**避免单一硬件依赖**，构建更开放的推理生态。

### 5. 基于项目背景的提交影响分析
vLLM的目标是提供**快速、廉价且易用**的LLM服务。昨日的提交紧密围绕这一目标：
- **“快速”**：通过优化推测解码、通信（非阻塞拷贝）、MoE内核以及修复性能相关问题（如ROCm的ROPE）来**保障和提升推理速度**。
- **“廉价”**：支持更多硬件平台（ROCm, Gaudi）为用户提供了更具**成本效益的硬件选择**。分布式推理（DP/EP）支持也能更好地利用集群资源，降低单次推理成本。
- **“易用”**：修复多模态模型、音频处理等Bug，并增强核心组件的稳定性，直接提升了**终端用户和开发者的体验**，减少了使用过程中的障碍。CI/CD的改进则提升了核心开发流程的顺畅度。

**总结**：昨日的更新是一次以**夯实基础、优化性能、扩展生态**为主的常规迭代。它没有引入颠覆性特性，而是专注于修复已知问题、深化对现有重要功能（如推测解码、MoE、多硬件支持）的优化，并推进下一代执行引擎（Model Runner V2）的开发。这符合一个成熟项目在稳定发展阶段的特点，旨在持续提升其作为**生产级LLM推理引擎**的可靠性、性能和适用范围。

## 详细提交记录

### [d15c3b9](https://github.com/vllm-project/vllm/commit/d15c3b90fc70ba8d787ee2b172caf5b978909fe9)

- **作者**: Nick Hill
- **时间**: 2026-03-03T23:31:59Z
- **提交信息**: [Core] Move save_tensorized_model logic to Worker (#35825)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [97286a2](https://github.com/vllm-project/vllm/commit/97286a20ed5803583c50af3dd1f45268346be0e8)

- **作者**: zhrrr
- **时间**: 2026-03-03T23:19:45Z
- **提交信息**: [Model Runner V2] support dp & ep for spec decoding (#35294)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Signed-off-by: zhuhaoran <zhuhaoran.zhr@alibaba-inc.com>
Co-authored-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [12b38c0](https://github.com/vllm-project/vllm/commit/12b38c0f4560e33b32cd5fbe50881d4d2e97470e)

- **作者**: Amr Mahdi
- **时间**: 2026-03-03T22:30:47Z
- **提交信息**: [CI/Build] Allow mounting AWS credentials for sccache S3 auth (#35912)

Signed-off-by: Amr Mahdi <amrmahdi@meta.com>

### [467886a](https://github.com/vllm-project/vllm/commit/467886a0c48b37552c8a2f3bdea99e96f2e98f8c)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-03T21:47:45Z
- **提交信息**: [Model Runner V2] Fix inputs_embeds=None bug for MM models (#35917)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [a9b8b13](https://github.com/vllm-project/vllm/commit/a9b8b13e5cdc52aa7f4472d4d21f178e3805bcdd)

- **作者**: bnellnm
- **时间**: 2026-03-03T21:29:57Z
- **提交信息**: [Bugfix] Fix misnamed parameter in compressed_tensors_moe.py (#35813)

Signed-off-by: Bill Nell <bnell@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [e721300](https://github.com/vllm-project/vllm/commit/e7213003cbf64d3f35b97d711eb595aa9e47039c)

- **作者**: Micah Williamson
- **时间**: 2026-03-03T20:57:34Z
- **提交信息**: [ROCm][CI] Fix TP size issue for `test_gpt_oss` (#35887)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [3a8eef5](https://github.com/vllm-project/vllm/commit/3a8eef5869b8997af22f7b204eba56f9e654875e)

- **作者**: Rohan Potdar
- **时间**: 2026-03-03T19:43:56Z
- **提交信息**: [ROCm][Bugfix]: Disable AITER Triton ROPE by default (#35601)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>

### [97995f6](https://github.com/vllm-project/vllm/commit/97995f6376fd3dae7a67624055ddf038233e181e)

- **作者**: Robert Shaw
- **时间**: 2026-03-03T18:39:50Z
- **提交信息**: [MoE Refactor] Create MK for TRTLLM Kernels (#32564)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Signed-off-by: Robert Shaw <rshaw@neuralmagic.com>
Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <rshaw@neuralmagic.com>

### [881a6b0](https://github.com/vllm-project/vllm/commit/881a6b011b76bddf159b1a635586064e34e221b0)

- **作者**: Robert Shaw
- **时间**: 2026-03-03T18:36:15Z
- **提交信息**: [CI] Temporarily Disable Llama4 MoE Refactor Test (#35870)

Signed-off-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [8e1fd5b](https://github.com/vllm-project/vllm/commit/8e1fd5baf0ff272936618bf578533d9aa7080a27)

- **作者**: Matthew Bonanni
- **时间**: 2026-03-03T17:26:44Z
- **提交信息**: [CI] Bump `num_speculative_tokens` to 3 in nightly DeepSeek tests (#35882)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [ae88468](https://github.com/vllm-project/vllm/commit/ae88468bcc88773d548122dc05f041a1b3670745)

- **作者**: JasonCohere
- **时间**: 2026-03-03T16:47:39Z
- **提交信息**: fix: Ensure invalid audio files return 400 error (#34715)

Signed-off-by: Jason Ozuzu <jasonozuzu@cohere.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [e05cb3b](https://github.com/vllm-project/vllm/commit/e05cb3b93e5db3afd510189651a128018c31c251)

- **作者**: ojhaanshika
- **时间**: 2026-03-03T16:35:34Z
- **提交信息**: TRTLLM gen-full attn Test Coverage (#34986)

Signed-off-by: Anshika Ojha <anshikao@nvidia.com>
Co-authored-by: Anshika Ojha <anshikao@gb-nvl-059-compute09.nvidia.com>

### [28ef9ba](https://github.com/vllm-project/vllm/commit/28ef9ba399340ea7013df8cd1c359b07acc0a302)

- **作者**: Lucas Wilkinson
- **时间**: 2026-03-03T15:21:57Z
- **提交信息**: [BugFix] Add support for MTP num_speculative_tokens > 1 with sparse MLA (#34552)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [fb7fdc4](https://github.com/vllm-project/vllm/commit/fb7fdc49c4a0c629fd92a5e49c08ec86f5dd8ff9)

- **作者**: TJian
- **时间**: 2026-03-03T14:24:21Z
- **提交信息**: [ROCm] [CI] Add new fusion test cases that are relevant to vLLM IR Ops (#34307)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>
Co-authored-by: vllmellm <vllm.ellm@embeddedllm.com>

### [ea46397](https://github.com/vllm-project/vllm/commit/ea463978bb987a4c15c9b51c0013d620a722aa67)

- **作者**: wang.yuqi
- **时间**: 2026-03-03T14:05:36Z
- **提交信息**: [Frontend][1/n] Improve pooling entrypoints | classify. (#35604)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [440f0e7](https://github.com/vllm-project/vllm/commit/440f0e7dc6cb0adfc9c3c98076939668b90c4bf2)

- **作者**: Li, Jiang
- **时间**: 2026-03-03T13:56:08Z
- **提交信息**: [Bugfix] Avoid src/dst as None in irecv/isend_tensor_dict (#35754)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [fd4a90f](https://github.com/vllm-project/vllm/commit/fd4a90f337f7fe188581d71d4d3ec712767320c0)

- **作者**: wang.yuqi
- **时间**: 2026-03-03T13:15:51Z
- **提交信息**: [CI] And PPL test for Qwen3.5. (#35853)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [ad9d09e](https://github.com/vllm-project/vllm/commit/ad9d09e2b8a601b50d07c76fb8736c2bbda2d6fb)

- **作者**: Thomas Parnell
- **时间**: 2026-03-03T12:15:43Z
- **提交信息**: [Perf] [Hybrid] Copy num_accepted_tokens in non-blocking way when not using prefix caching (#35442)

Signed-off-by: Thomas Parnell <tpa@zurich.ibm.com>

### [4beebfd](https://github.com/vllm-project/vllm/commit/4beebfd14650b1c6a687e7ab496d501423a0e50d)

- **作者**: Szymon Reginis
- **时间**: 2026-03-03T11:48:24Z
- **提交信息**: [CI/Build][Intel] Add new performance benchmarks for Intel Gaudi 3 (#31025)

Signed-off-by: Szymon Reginis <sreginis@habana.ai>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>



---

