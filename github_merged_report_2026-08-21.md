# GitHub Stars 合并报告 - 2026-08-21

**合并日期**: 2026-08-22
**监控日期**: 2026-08-21
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


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2167
- **最后更新**: 2026-08-21T09:07:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2709
- **最后更新**: 2026-08-21T14:22:22Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: STwangyingrui, Watebear

## AI分析总结

### 主要更新类型
本次提交以**性能优化**和**平台适配**为核心，包含两项性能优化、一项新平台支持及一项功能分析，无Bug修复或文档更新。

### 关键变更点与项目方向
1. **MiniMax-H3 AdaLN输出缓存**（f8aee98）：跨请求缓存按时间步计算的AdaLN输出，跳过重复投影、TP通信和块卸载权重传输，并在动态LoRA更新后自动刷新。这直接服务于项目“轻量级视频生成推理”目标，减少重复计算开销。
2. **MiniMax-H3 VAE时空分块并行**（00a89ad）：统一时空分块池跨rank均衡分配，8卡768×1344下任务级效率从87.5%提升至98.0%（5s）和99.3%（15s），消除因视频时长/分辨率导致的效率锯齿。该优化强化了框架对多分辨率、多时长视频的稳定高效推理能力。
3. **昇腾平台稠密模型支持与MoE重构**（0714ee8）：新增昇腾平台稠密模型推理能力，并重构MoE模块及配置，扩大硬件生态覆盖，提升模块可维护性。
4. **Hunyuan3D绘制模型分析**（127a715）：新增绘制模型推理性能分析功能，为后续优化提供数据支撑，拓展3D生成场景。

### 项目影响与潜在意义
- **推理效率显著提升**：AdaLN缓存和VAE并行优化直接降低计算与通信开销，尤其对长视频（15s）场景提升明显，增强框架在高分辨率、长时长视频生成中的竞争力。
- **硬件生态扩展**：昇腾平台支持使框架适配国产AI芯片，符合“轻量级”跨平台定位，吸引更广泛用户。
- **架构可维护性增强**：MoE模块重构和配置梳理降低后续扩展成本，为多模型、多硬件支持奠定基础。
- **3D能力铺垫**：Hunyuan3D分析为未来3D视频生成优化提供依据，拓宽应用边界。

### 值得关注的技术点
- **跨请求缓存机制**：需确保缓存与动态LoRA更新的正确性同步，体现对模型动态性的精细处理。
- **时空分块并行策略**：统一分块池设计平衡了计算负载，避免了传统按clip划分导致的效率波动，是并行优化中的创新点。
- **昇腾平台适配**：涉及算子映射和内存管理差异，需关注其与CUDA后端的性能对比。

### 对项目发展的影响
结合README中“轻量级视频生成推理框架”定位，本次提交通过**核心模型（MiniMax-H3）的深度优化**、**硬件平台扩展**和**3D场景探索**，强化了框架在性能、兼容性和功能广度上的优势。性能提升直接增强用户吸引力，昇腾支持打开国产化市场，而3D分析则预示未来多模态生成方向。整体上，这些提交推动项目向**更高效、更普适、更多元**的方向演进，巩固其在视频生成推理领域的领先地位。

## 详细提交记录

### [f8aee98](https://github.com/ModelTC/LightX2V/commit/f8aee98b5462cca8d7288888146ebd95592bf266)

- **作者**: STwangyingrui
- **时间**: 2026-08-21T09:45:44Z
- **提交信息**: perf(minimax_h3): cache AdaLN outputs across requests (#1413)

Caches MiniMax-H3 AdaLN outputs by timestep and reuses them across
requests. Cache hits skip repeated AdaLN projection, TP communication,
and block-offload weight transfers. Cached outputs automatically refresh
after dynamic LoRA updates to preserve correctness.

### [00a89ad](https://github.com/ModelTC/LightX2V/commit/00a89ad50e48b0037b58ab224969c43d0b645ee3)

- **作者**: STwangyingrui
- **时间**: 2026-08-21T09:44:42Z
- **提交信息**: Improve MiniMax-H3 VAE load balance with spatiotemporal tile parallelism (#1394)

Balances a unified temporal-spatial tile pool across ranks. On 8 GPUs at
768×1344, task-level efficiency improves from 87.5% to 98.0% for 5s and
99.3% for 15s videos. It also removes the coarse efficiency sawtooth
caused by varying clip counts across video durations and resolutions.

### [0714ee8](https://github.com/ModelTC/LightX2V/commit/0714ee81d5e4e67e52f9ddf95595611c35e17f0e)

- **作者**: Watebear
- **时间**: 2026-08-21T09:35:11Z
- **提交信息**: feat(neopp/ascend): 1. support dense model in ascend platform; 2.refactor moe module and configs (#1396)

### [127a715](https://github.com/ModelTC/LightX2V/commit/127a7156d03af01c33ab30b42f0ea2056b22c809)

- **作者**: Watebear
- **时间**: 2026-08-21T09:31:19Z
- **提交信息**: feat(hunyuan3d): profile paint model inference (#1343)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2199
- **最后更新**: 2026-08-20T21:19:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6206
- **最后更新**: 2026-08-21T21:58:57Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Xuanyu Zhang, eigen

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
两笔提交均为**功能新增**，分别针对Mamba状态更新和MoE激活函数，属于内核层面的能力扩展。

### 2. 关键变更点与项目方向
- **提交1（#4616）**：为Blackwell架构新增selective state update后端，引入Cake实现作为替代路径。这与FlashInfer“高性能GPU推理内核”的定位高度一致，通过多后端策略提升硬件适配性。
- **提交2（#4460）**：在CUTLASS fused-MoE后端中加入SiTU-GLU激活函数，覆盖SM89/90/100/103/120全系架构。这扩展了MoE模块的激活函数生态，对齐Kimi-K3等前沿模型需求。

### 3. 项目影响与潜在意义
- 提交1的基准测试显示**几何平均1.076倍加速**，在动态调度场景最高达1.30倍，且对SGLang捕获布局的Granite NGRAM内核有1.15-1.32倍提升，直接提升实际推理吞吐。
- 提交2使FlashInfer能支持采用SiTU-GLU的MoE模型（如Kimi-K3），填补了激活函数支持空白，增强对最新模型架构的兼容性，扩大潜在用户群。

### 4. 值得关注的技术点
- **提交1**：采用“auto/simple/vertical”调度策略，自动选择最优路径；针对Blackwell架构优化，且诊断数据表明forced vertical存在4.89倍性能差距，说明调度选择对性能影响显著。
- **提交2**：使用`2·sigmoid(2z)−1`近似tanh以避免`tanh.approx.f32`在`linear_beta=25`时的误差放大；支持per-expert参数张量，提升灵活性；重构参数分发逻辑减少代码重复。

### 5. 对项目发展的影响
两笔提交共同强化了FlashInfer作为**多架构、多模型覆盖的高性能推理库**的定位。提交1巩固了其在Blackwell这一最新硬件上的性能优势，提交2则扩展了模型支持面。结合README强调的“High-Performance GPU Kernels for Inference”目标，这些变更直接服务于提升推理速度与模型兼容性两大核心价值，有助于吸引更多生产环境用户，并保持与前沿模型（如Kimi-K3）和硬件（如GB300）的同步演进。

## 详细提交记录

### [46fc99b](https://github.com/flashinfer-ai/flashinfer/commit/46fc99b9773bc98832a8610b5d789d3bcdafde85)

- **作者**: eigen
- **时间**: 2026-08-21T20:25:33Z
- **提交信息**: feat(cake_mamba): add Blackwell selective state update backend (#4616)

| Shape | FlashInfer (ms) | Cake (ms) | Speedup |
|---|---:|---:|---:|
| `sample_stp_bf16` | 0.046816 | 0.046529 | 1.006168x |
| `sample_stp_state_fp32` | 0.085985 | 0.084544 | 1.017044x |
| `sample_stp_z` | 0.048033 | 0.047136 | 1.019030x |
| `sample_stp_softplus` | 0.046849 | 0.046432 | 1.008981x |
| `sample_stp_z_softplus` | 0.048064 | 0.047136 | 1.019688x |
| `sample_stp_ratio1` | 0.010208 | 0.009312 | 1.096220x |
| `sample_stp_ratio16` | 0.046656 | 0.046528 | 1.002751x |
| `sample_mtp1` | 0.048064 | 0.045696 | 1.051821x |
| `sample_mtp2` | 0.049088 | 0.047744 | 1.028150x |
| `sample_stp_b256` | 0.167392 | 0.163616 | 1.023078x |
| `sample_stp_b128` | 0.087328 | 0.086720 | 1.007011x |
| `sweep_bfloat16_auto_b1` (same shape; auto selects simple) | 0.005120
| 0.003936 | 1.300813x |
| `sweep_bfloat16_horizontal_b1024` | 1.165732 | 1.150692 | 1.013070x |
| `dynamic_dump_b1_t1_prev0` | 0.003424 | 0.002976 | 1.150538x |
| `dynamic_dump_b1_t4_prev2` | 0.004160 | 0.003456 | 1.203704x |
| `dynamic_dump_b1_t8_prev4` | 0.004960 | 0.004128 | 1.201550x |
| `dynamic_dump_b1_t8_prev8` | 0.004960 | 0.004256 | 1.165414x |
| `dynamic_dump_b8_t2_prev1` | 0.005056 | 0.004576 | 1.104895x |
| **Geomean (18 production-comparable rows; forced-schedule diagnostics
excluded)** | | | **1.075556x** |

| Same B1 sweep shape algorithm check | FlashInfer (ms) | Cake (ms) |
Speedup |
|---|---:|---:|---:|
| `auto` (selects `simple`) | 0.005120 | 0.003936 | 1.300813x |
| forced `simple` | 0.005120 | 0.003936 | 1.300813x |
| forced `vertical` diagnostic | 0.019232 | 0.003936 | 4.886179x |

| Granite NGRAM T6 device kernel on captured SGLang layouts | FlashInfer
auto/simple (us) | Cake (us) | Speedup |
|---:|---:|---:|---:|
| 1 | 5.280 | 4.000 | 1.320000x |
| 2 | 6.272 | 5.184 | 1.209877x |
| 3 | 7.648 | 6.336 | 1.207071x |
| 4 | 8.448 | 7.360 | 1.147826x |

| Granite 4.0 H Micro NGRAM T6 GB300 serving | Min speedup | Median
speedup | Max speedup |
|---|---:|---:|---:|
| C1, 6/6 paired rounds | 1.006030x | 1.007661x | 1.010124x |
| C4, 6/6 paired rounds | 1.003363x | 1.006004x | 1.024688x |

### SGLang validation commands

```bash
# The validation checkout forwards SGLANG_MAMBA_SSU_DECODE_BACKEND to
# flashinfer.mamba.selective_state_update(..., backend=...).
MODEL=ibm-granite/granite-4.0-h-micro
REVISION=d5f01a3ea75f088947be3aae039f4ad52837dfde
BACKEND=flashinfer  # Repeat the accuracy commands with BACKEND=cake.

SGLANG_MAMBA_SSU_DECODE_BACKEND="${BACKEND}" \
python3 -m sglang.launch_server \
  --model-path "${MODEL}" \
  --served-model-name "${MODEL}" \
  --revision "${REVISION}" \
  --trust-remote-code \
  --attention-backend triton \
  --mamba-backend flashinfer \
  --mamba-ssm-dtype bfloat16 \
  --speculative-algorithm NGRAM \
  --speculative-num-draft-tokens 6 \
  --speculative-eagle-topk 1 \
  --speculative-ngram-min-bfs-breadth 1 \
  --speculative-ngram-max-bfs-breadth 1 \
  --cuda-graph-bs-decode 1 2 3 4 \
  --max-running-requests 4 \
  --max-mamba-cache-size 64 \
  --disable-radix-cache \
  --mem-fraction-static 0.70 \
  --random-seed 20260819 \
  --host 127.0.0.1 \
  --port 30000 >"${BACKEND}-server.log" 2>&1 &
SERVER_PID=$!
until curl -fsS http://127.0.0.1:30000/health >/dev/null; do sleep 5; done

python3 .validation/fixed_eval.py \
  --output "${BACKEND}-warmup.json" \
  --repeats 1 \
  --max-new-tokens 128 \
  --concurrency 1

python3 .validation/fixed_eval.py \
  --output "${BACKEND}-fixed.json" \
  --repeats 5 \
  --max-new-tokens 128 \
  --concurrency 1

python3 -m sglang.test.run_eval \
  --base-url http://127.0.0.1:30000 \
  --model "${MODEL}" \
  --eval-name gsm8k \
  --api completion \
  --max-tokens 512 \
  --num-examples 50 \
  --num-threads 1

kill -INT "${SERVER_PID}"
wait "${SERVER_PID}"

python3 .validation/ssu_real_model_perf.py \
  --model-path "${MODEL}" \
  --tokenizer-path "${MODEL}" \
  --served-model-name "${MODEL}" \
  --revision "${REVISION}" \
  --sglang-source-root /path/to/sglang \
  --flashinfer-source-root /path/to/flashinfer \
  --output-dir /tmp/ssu-real-model-perf \
  --concurrencies 1 4 \
  --rounds 6 \
  --num-prompts 64 \
  --output-len 512 \
  --warmup-prompts 16 \
  --warmup-output-len 128 \
  --require-every-pair-speedup
```

| Accuracy check | FlashInfer | Cake | Result |
|---|---:|---:|---:|
| Fixed deterministic generations | 40 | 40 | 40/40 exact text and token
IDs |
| Selected-logprob max / mean / median absolute delta | 0 | 0 | 0 |
| Fixed-cohort aggregate output throughput (tok/s) | 456.5208 | 472.3884
| 1.034758x |
| GSM8K-50 | 0.80 | 0.80 | equal |

| CUDA Graph route proof | Raw T6 hits | Graph fallback | Total fallback
|
|---:|---:|---:|---:|
| C1 | 36 | 0 | 0 |
| C4 | 144 | 0 | 0 |

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [b460bc0](https://github.com/flashinfer-ai/flashinfer/commit/b460bc00cb373541102d2155aec35bd626e522ce)

- **作者**: Xuanyu Zhang
- **时间**: 2026-08-21T19:39:35Z
- **提交信息**: feat(moe): add SiTU-GLU activation to the CUTLASS fused-MoE backend (#4460)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds SiTU-GLU activation support to the CUTLASS fused-MoE backend,
covering all SM variants (SM89/90/100/103/120) via the shared activation
kernel code.

- Adds `ActivationType::Situ = 10` enum value (consistent with the
TRT-LLM Gen path in #4180)
- Implements `SituAdaptor` with `beta` (default 4.0) and `linear_beta`
(default 25.0) per the SiTU paper (Kimi-K3)
- Uses `2·sigmoid(2z)−1` for tanh (matching the CuTe-DSL path in #4009)
— avoids `tanh.approx.f32` error amplification at `linear_beta=25`
  - Supports per-expert `situ_beta` / `situ_linear_beta` tensors
- Refactors per-expert activation param dispatch into
`setPerExpertActivationParams()` / `hasPerExpertActivationParams()`
helpers (reduces duplication across `doGatedActivationKernel` and
`doActivationKernel`)
  - Tests both default and per-expert parameters in BF16 and FP8

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
- [x] `pytest tests/moe/test_trtllm_cutlass_fused_moe.py` — SiTU cases
in both `test_moe` (BF16) and `test_moe_fp8`

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added SiTU-GLU activation support for fused Mixture-of-Experts
operations.
  - Added optional global or per-expert SiTU scaling parameters.
- Added support across standard, low-latency, and FP8 MoE execution
paths.
- Added default SiTU scaling values when custom parameters are not
provided.
  - Added validation for per-expert scaling inputs.

- **Tests**
- Added coverage for default and per-expert SiTU scales, including FP8
execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Mickael Seznec <mickael@mistral.ai>
Co-authored-by: Claude <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4021
- **最后更新**: 2026-08-21T21:58:13Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: Shao Duan, Kaiqin Kong, William Lin

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **性能优化**（3项）：VAE解码、文本编码器内存、Sol-Engine融合
- **功能新增**（1项）：FastH3预览版few-step示例及64-token-tile推理路径
- **Bug修复**（1项）：Triton block-sparse反向logit缩放问题
- **代码整理**（1项）：AdaLN转换器迁移至脚本目录

### 2. 关键变更点与项目方向
所有提交均围绕 **MiniMax-H3模型** 展开，这是FastVideo近期重点支持的视频生成架构。核心方向是：
- **推理效率提升**：通过VAE解码优化、文本编码器内存压缩、Sol-Engine算子融合，降低显存占用和计算延迟
- **功能扩展**：新增FastH3预览版的few-step采样示例，支持64-token-tile的VSA-H3推理路径，提升长视频生成能力
- **代码规范化**：将AdaLN转换器从主流程移至独立脚本，保持代码库整洁

### 3. 项目影响与潜在意义
- **降低使用门槛**：few-step示例和内存优化使MiniMax-H3在消费级GPU上运行成为可能
- **加速推理**：Sol-Engine融合和VAE优化可显著缩短视频生成时间，提升用户体验
- **生态完善**：Bug修复（bf16预缩放）确保混合精度训练/推理的数值稳定性，增强可靠性

### 4. 值得关注的技术点
- **Triton block-sparse backward logit缩放修复**：涉及bf16 K矩阵预缩放，对大规模稀疏注意力训练至关重要
- **64-token-tile VSA-H3路径**：一种新的token分块策略，可能影响长序列视频生成的效率与质量平衡
- **Sol-Engine opt-in融合**：提供可选的算子融合方案，用户可根据硬件灵活启用

### 5. 对项目发展的影响
FastVideo定位为**高性能视频生成框架**，这些提交强化了其在MiniMax-H3这一前沿模型上的技术领先性。通过持续优化推理路径和内存效率，项目正朝着**“让高质量视频生成在更广泛硬件上可用”**的目标迈进。同时，代码整理和bug修复体现了项目对工程质量的重视，为后续社区贡献和模型扩展奠定了稳定基础。整体来看，这批提交是FastVideo在**效率与可用性**维度上的重要推进。

## 详细提交记录

### [2f3d407](https://github.com/hao-ai-lab/FastVideo/commit/2f3d4074064e4d86f99dc784ebbaa296e6f5925f)

- **作者**: Junda Su
- **时间**: 2026-08-21T21:57:32Z
- **提交信息**: [perf] Optimize MiniMax H3 VAE decoding (#1734)

### [bcffa40](https://github.com/hao-ai-lab/FastVideo/commit/bcffa4026e5ef62d14bf0b21ff876a5f6d17a8de)

- **作者**: Kaiqin Kong
- **时间**: 2026-08-21T21:57:06Z
- **提交信息**: [perf] Optimize MiniMax-H3 text encoder memory (#1732)

### [6d6a10b](https://github.com/hao-ai-lab/FastVideo/commit/6d6a10be7aabaf38b4363daa27f8a7a9e8f34465)

- **作者**: William Lin
- **时间**: 2026-08-21T17:40:09Z
- **提交信息**: [feat] FastVideo-Minimax-FastH3-Preview few-step example + 64-token-tile VSA-H3 inference path (#1731)

### [73dd105](https://github.com/hao-ai-lab/FastVideo/commit/73dd105f3d71f360cabf2a522cfc335f0f9eb271)

- **作者**: Kaiqin Kong
- **时间**: 2026-08-21T17:39:28Z
- **提交信息**: [perf] Add opt-in MiniMax-H3 Sol-Engine fusions (#1735)

### [56d4a60](https://github.com/hao-ai-lab/FastVideo/commit/56d4a6074f262d05b288d7603bc631979b0f2c93)

- **作者**: William Lin
- **时间**: 2026-08-21T09:50:06Z
- **提交信息**: [bugfix] fastvideo-kernel: fix Triton block-sparse backward logit scaling (bf16 K pre-scaling) (#1730)


Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [c4ad422](https://github.com/hao-ai-lab/FastVideo/commit/c4ad4227c09a84387f340d803607042df758e170)

- **作者**: Shao Duan
- **时间**: 2026-08-21T07:15:00Z
- **提交信息**: [misc] MiniMax-H3: move the AdaLN converter into scripts/checkpoint_conversion (#1712)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34347
- **最后更新**: 2026-08-21T11:37:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
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


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12974
- **最后更新**: 2026-08-21T01:58:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32237
- **最后更新**: 2026-08-21T21:49:22Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 17
- **主要提交者**: jasonjk-park, Shangming Cai, Hank Han

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本次提交涵盖**功能新增**（多适配器LoRA推理、扩散模型Peft LoRA加载、Granite SWA支持）、**Bug修复**（量化QKV缩放、注意力后端回退、H2D拷贝阻塞、GRPC归一化）、**性能优化**（SANA-Video线性注意力加速、CUDA图优化、避免阻塞拷贝）、**重构**（disagg模块死代码清理、mem_cache分层重构、EPD重构）、**文档更新**（安装版本、DSPARK选项、内存缓存层映射）及**AMD ROCm适配**（FlyDSL内核、AITER版本更新）。

### 2. 关键变更点与项目方向

- **多适配器LoRA与投机解码结合**：支持EAGLE/NEXTN/DFLASH/DSPARK多种投机解码策略下多LoRA适配器并行，显著增强多租户场景灵活性。
- **扩散模型生态扩展**：Peft LoRA加载、量化修复、注意力后端回退，配合SANA-Video加速，强化多模态生成能力。
- **disagg模块系统清理**：提取辅助函数、合并重复分支、删除死代码，提升可维护性，为后续功能迭代铺路。
- **内存缓存分层重构**：引入层映射和放置规则，优化缓存管理，是长期架构演进的一部分。
- **EPD重构**：大规模重构实验性并行解码方案，可能影响推理性能核心路径。

### 3. 项目影响与潜在意义

- **多适配器LoRA支持**是生产级部署的关键能力，直接提升商业落地价值。
- **扩散模型修复与加速**扩大模型覆盖面，吸引更多多模态用户。
- **死代码清理与重构**降低维护成本，提升开发效率，为社区贡献者降低入门门槛。
- **AMD ROCm适配**持续跟进，扩大硬件生态兼容性。

### 4. 值得关注的技术点

- **避免阻塞H2D拷贝**：用`index_fill_`替代全量映射，优化GPU内存访问模式。
- **CUDA_MODULE_LOADING不覆盖**：尊重用户环境配置，避免潜在兼容性问题。
- **mapped-weight store不持有参数**：减少内存引用，优化生命周期管理。
- **LongCat breakable CUDA graphs**：提升长序列场景下的图捕获灵活性。
- **FlyDSL 0.3.0兼容**：紧跟AMD内核库演进。

### 5. 对项目发展的影响

SGLang正从纯LLM推理引擎向**多模态统一推理平台**演进。本次提交中扩散模型相关改动占比最高，表明团队正积极拓展文生图/视频能力；同时多适配器LoRA和投机解码的结合，强化了其在**高吞吐、多租户生产环境**中的竞争力。disagg和mem_cache的系统性重构，显示项目在追求功能丰富的同时，也注重架构健康度。AMD ROCm的持续适配则体现其**跨硬件平台**的战略布局。整体来看，项目正朝着**功能全面、架构清晰、硬件兼容**的方向稳步前进。

## 详细提交记录

### [7d89325](https://github.com/sgl-project/sglang/commit/7d893255c359bb8ab74d2870c8ac865fb57230d6)

- **作者**: Yanbin Jiang
- **时间**: 2026-08-21T21:21:53Z
- **提交信息**: [Spec][LoRA] Support multi-adapter LoRA with EAGLE/NEXTN/DFLASH/DSPARK speculative decoding (#34337)

### [590b11a](https://github.com/sgl-project/sglang/commit/590b11a5efb55a11082eda9249d95f889e26440e)

- **作者**: Hank Han
- **时间**: 2026-08-21T21:09:27Z
- **提交信息**: [Runtime] Don't override CUDA_MODULE_LOADING (#35711)

Co-authored-by: TRAE CLI <traecli@bytedance.com>

### [4d42def](https://github.com/sgl-project/sglang/commit/4d42deff0a2796ce64c41776c41077deaabd60c2)

- **作者**: sglang-bot
- **时间**: 2026-08-21T20:24:03Z
- **提交信息**: chore: bump docs install version to 0.5.18 (#35911)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [05c584c](https://github.com/sgl-project/sglang/commit/05c584c44fb0450c894cf9d08a7827c10cd5b2c5)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-21T18:50:55Z
- **提交信息**: docs: add DSPARK speculative decoding option to Ling-3.0-flash cookbook (#35861)

### [729a050](https://github.com/sgl-project/sglang/commit/729a050ea36afeb7213c653e507e0e3d5737b6fd)

- **作者**: Shangming Cai
- **时间**: 2026-08-21T18:30:33Z
- **提交信息**: refactor(disagg): extract _all_reduce_polls helper (#35886)

### [c373562](https://github.com/sgl-project/sglang/commit/c3735625de58340302eb369a55a8f83b00325d9a)

- **作者**: Connor Carpenter
- **时间**: 2026-08-21T18:29:52Z
- **提交信息**: fix(grpc): derive choice count before normalization (#35778)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>

### [61c2da4](https://github.com/sgl-project/sglang/commit/61c2da42bb656303425d8af79b71e0bcdb0e7d0c)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-21T18:22:11Z
- **提交信息**: [Fix] Pass Anthropic thinking history as reasoning_content for custom chat encoders (#35480)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [70983bd](https://github.com/sgl-project/sglang/commit/70983bd7dbd54929f1d76fd59227fa37876277a3)

- **作者**: Davis Wertheimer
- **时间**: 2026-08-21T18:13:15Z
- **提交信息**: Add SGLang Granite SWA support via existing Granite models (#35794)

Signed-off-by: Davis Wertheimer <davis.wertheimer@ibm.com>

### [0bdd28d](https://github.com/sgl-project/sglang/commit/0bdd28d487432f5b964fbd25a36e80c0d86657ad)

- **作者**: Shuwen Wang
- **时间**: 2026-08-21T16:35:07Z
- **提交信息**: [mem_cache] docs: add a layer map and placement rules (#35643)

Co-authored-by: ispobock <ispobaoke@gmail.com>

### [a7ec6b9](https://github.com/sgl-project/sglang/commit/a7ec6b97f786892a73d1edfc2e35b09c37997b6c)

- **作者**: Shuwen Wang
- **时间**: 2026-08-21T15:29:59Z
- **提交信息**: Restructure mem_cache auto-labels by layer (#25122)

Co-authored-by: ispobock <ispobaoke@gmail.com>

### [8658d00](https://github.com/sgl-project/sglang/commit/8658d00764e5970228816191114c290b2d0fa215)

- **作者**: Mick
- **时间**: 2026-08-21T14:58:59Z
- **提交信息**: [diffusion] feat: support loading peft lora (#35868)

### [0447ade](https://github.com/sgl-project/sglang/commit/0447ade32696e6ee84b3671feac43c3d5d070472)

- **作者**: li_max
- **时间**: 2026-08-21T14:56:44Z
- **提交信息**: [diffusion] fix: fall back to a component's default attention backend (#35796)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [932f632](https://github.com/sgl-project/sglang/commit/932f63215849cd1b8d95e41d97803c65fc23ef5c)

- **作者**: 王鹤男
- **时间**: 2026-08-21T14:56:03Z
- **提交信息**: [diffusion] fix: do not warn that the recommended short edge is unverified (#35745)

### [a41da99](https://github.com/sgl-project/sglang/commit/a41da991c8f49556d0daed2445ee0b72800ff22e)

- **作者**: Shangming Cai
- **时间**: 2026-08-21T14:11:31Z
- **提交信息**: refactor(disagg): collapse duplicated branches in get_kv_class (#35847)

### [5ecd6d7](https://github.com/sgl-project/sglang/commit/5ecd6d794d093c9f6b8f6691a92b1da11df78a72)

- **作者**: 王鹤男
- **时间**: 2026-08-21T14:10:50Z
- **提交信息**: [diffusion] fix: fix quantized qkv scales and missing-param policy for minimax-h3 (#35740)

### [4f343ab](https://github.com/sgl-project/sglang/commit/4f343abc13e13f336f4d237dfacf71be7306ebe2)

- **作者**: Shangming Cai
- **时间**: 2026-08-21T14:09:25Z
- **提交信息**: refactor(disagg): remove unreferenced dead code (#35838)

### [5a46d65](https://github.com/sgl-project/sglang/commit/5a46d657b7ea8de932266dc0a084d2217c78b168)

- **作者**: Mick
- **时间**: 2026-08-21T13:05:40Z
- **提交信息**: [diffusion] refactor: resolve lora weight sources deterministically (#35774)

### [5206f11](https://github.com/sgl-project/sglang/commit/5206f115433b60699abf486e77296448f3b46e7d)

- **作者**: Mick
- **时间**: 2026-08-21T13:02:21Z
- **提交信息**: [diffusion] fix: stop the mapped-weight store from holding the parameter itself (#35813)

### [dad6fd0](https://github.com/sgl-project/sglang/commit/dad6fd0f04556a9a2c09fc08388ecee45ed5a33f)

- **作者**: Shangming Cai
- **时间**: 2026-08-21T10:12:23Z
- **提交信息**: refactor(disagg): remove dead get_embedding_port (#35844)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [39d4d65](https://github.com/sgl-project/sglang/commit/39d4d65a518b007465c02e5916d40eb80a9d7a14)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-21T10:05:43Z
- **提交信息**: [diffusion] Accelerate SANA-Video linear attention in quality=high (#35728)

### [a5c52a9](https://github.com/sgl-project/sglang/commit/a5c52a9358560a3f4e4667057ffa4585a4618ad1)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-21T09:59:16Z
- **提交信息**: [diffusion] Enable LongCat breakable CUDA graphs (#35724)

### [e7a37c8](https://github.com/sgl-project/sglang/commit/e7a37c85505ff0a4ba643574704ea6de36c631c5)

- **作者**: Shangming Cai
- **时间**: 2026-08-21T09:58:35Z
- **提交信息**: refactor(disagg): remove dead build_and_send_encode_request (#35843)

### [0db2c53](https://github.com/sgl-project/sglang/commit/0db2c53deca12715d209ffbd46bdfafdfd5a5d35)

- **作者**: jasonjk-park
- **时间**: 2026-08-21T09:00:13Z
- **提交信息**: Fix overlap prebuilt row reuse race (#35748)

### [896acc8](https://github.com/sgl-project/sglang/commit/896acc8860ff60dd0471328bf598692bc38ee242)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-21T08:23:26Z
- **提交信息**: [Fix] Clear full-to-SWA mapping with `index_fill_` to avoid a blocking H2D copy (#35773)

### [4c98759](https://github.com/sgl-project/sglang/commit/4c98759c73a9b2a657290149b5f30e438f0ae7eb)

- **作者**: Bingxu Chen
- **时间**: 2026-08-21T08:13:21Z
- **提交信息**: [AMD] fix(rocm): support flydsl 0.3.0 in the FlyDSL fused norm kernel (#34536)

Co-authored-by: Bingxu Chen <195740905+bingxche@users.noreply.github.com>
Co-authored-by: thomawan <thomawan@amd.com>

### [8ff9c2b](https://github.com/sgl-project/sglang/commit/8ff9c2b2276e388f94c88be08c644554fa384b6f)

- **作者**: Shuwen Wang
- **时间**: 2026-08-21T07:59:15Z
- **提交信息**: [mem_cache][9/N] refactor: move DSAIndexerPoolHost to pool_host.dsa (#35306)

### [8a123cb](https://github.com/sgl-project/sglang/commit/8a123cbd0e1c1ca735615a071d46879b72f6235d)

- **作者**: siyu
- **时间**: 2026-08-21T07:22:48Z
- **提交信息**: [Refactor] New EPD (#30398)

Co-authored-by: Yuang Chen <1131578721@qq.com>
Co-authored-by: Yuang Chen <cya539102@antgroup.com>
Co-authored-by: ZhengWG <zwg0606@gmail.com>

### [6a12583](https://github.com/sgl-project/sglang/commit/6a125836798c5a3e3a6ebd217a9cd8afb4b3b4d9)

- **作者**: Bingxu Chen
- **时间**: 2026-08-21T07:02:17Z
- **提交信息**: [AMD] Update ROCm AITER pin to c16d44b (#35810)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1253
- **最后更新**: 2026-08-21T15:28:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 89654
- **最后更新**: 2026-08-21T22:25:19Z

## 提交统计

- **昨日提交总数**: 46
- **提交者数量**: 37
- **主要提交者**: DCo, kliuae, Hongxia Yang

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型

本批次共46个提交，涵盖**Bug修复**（约15个）、**性能优化**（约8个）、**CI/测试改进**（约8个）、**功能新增**（约5个）、**代码回退**（4个）、**文档更新**（2个）及**安全修复**（1个）。其中AMD ROCm相关贡献占比最高，约10个提交，体现vLLM对多硬件平台支持的持续投入。

## 二、关键变更点与项目方向

1. **模型支持扩展**：新增Kimi K3、Hunyuan V1/VL、DeepSeek V4等模型的优化实现，包括MXFP4 top-k融合、KDA prefill fused kernels等，直接提升特定模型的推理效率。同时回退了两项相关优化，说明性能调优仍在迭代中。

2. **注意力机制优化**：FlashInfer后端多项修复（LSE归一化、XQA回退机制、DSpark DCP清理），提升长上下文场景下的数值稳定性和兼容性。

3. **多硬件适配**：ROCm平台获得大量CI稳定化、kernel优化（TileLang HIP符号检查、AITER ops）和测试增强；XPU平台新增mrope支持和CI并行化，体现vLLM跨平台战略。

4. **安全与稳定性**：修复decoder prompt长度验证绕过漏洞、前缀缓存加盐文档化、HTTP错误码规范化，强化生产环境可靠性。

## 三、项目影响与潜在意义

- **性能提升**：DSv4自适应topk宽度和K3 MXFP4融合预计带来约5%端到端延迟降低，对大规模部署有直接收益。
- **生态兼容性**：Anthropic参数转发、Cohere工具调用修复、GLM稀疏注意力DCP支持，扩大框架对主流模型的适配范围。
- **工程规范化**：编译缓存设备索引修复、批量请求URL验证、确定性MoE合并等，提升系统可维护性和可复现性。

## 四、值得关注的技术点

1. **编译缓存设备索引回归修复**（#53304/#38962）：解决多GPU环境下缓存路径冲突问题，对分布式推理至关重要。
2. **LoRA int32索引溢出修复**：针对长上下文场景的数值边界问题，具有通用参考价值。
3. **FlashInfer XQA回退机制**：当KV-cache组的head_dim不匹配时自动降级，增强鲁棒性。
4. **b12x FP4 MoE后端**：新增量化kernel，扩展低精度推理选项。

## 五、对项目发展的影响

vLLM正沿着**多硬件支持、模型广度扩展、性能极致优化**三条主线快速演进。AMD ROCm的密集投入表明其已成为与CUDA同等重要的目标平台；频繁的模型特定优化（Kimi、DeepSeek、Hunyuan）显示vLLM正从通用框架向"模型-硬件协同优化"方向深化；安全修复和CI稳定性工作则夯实了其作为生产级LLM服务基础设施的定位。整体来看，项目在保持快速迭代的同时，正逐步强化工程成熟度，为更广泛的企业级部署奠定基础。

## 详细提交记录

### [a556f3f](https://github.com/vllm-project/vllm/commit/a556f3fccb701e5618d84d547ff454c56a1bfdfb)

- **作者**: Maroon Ayoub
- **时间**: 2026-08-21T22:23:21Z
- **提交信息**: Forward Anthropic vllm_xargs to sampling params (#53308)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>

### [f94dcde](https://github.com/vllm-project/vllm/commit/f94dcde5c53b1930f98776e3793dd460d237d054)

- **作者**: andrewbcohere
- **时间**: 2026-08-21T22:23:17Z
- **提交信息**: Fix Cohere ChatV2 citation and tool handling issues (#52175)

Signed-off-by: Andrew Berneshawi <andrewberneshawi@cohere.com>

### [f37d586](https://github.com/vllm-project/vllm/commit/f37d5868b9530497c9474f4850fdd0577f4dad79)

- **作者**: stefankoncarevic
- **时间**: 2026-08-21T21:17:42Z
- **提交信息**: [CI/Build][ROCm] Run the TileLang HIP symbol checks in their own interpreter (#53117)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [e3f6026](https://github.com/vllm-project/vllm/commit/e3f60265032e7c1e158a749d82a8c4dad62f941a)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-21T20:39:58Z
- **提交信息**: Revert "Remove native Hunyuan V1 and VL implementations" (#53296)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [592e06f](https://github.com/vllm-project/vllm/commit/592e06f2ae115cbb0f7e2e1e776c255a3fe6c3c1)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-21T20:34:13Z
- **提交信息**: Revert "[ROCm][Perf] Kimi-K3 Fused kernels for KDA prefill" (#53294)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [0a3a4f7](https://github.com/vllm-project/vllm/commit/0a3a4f7f35b7e6e70a1804742dec65b6bec1d2fa)

- **作者**: Lucas Wilkinson
- **时间**: 2026-08-21T20:22:01Z
- **提交信息**: [Bugfix][KV Connector][NIXL] Support PCP producers (#52779)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [3e47a9a](https://github.com/vllm-project/vllm/commit/3e47a9a8240d2b91498d8c97a925b58e6c29ff9f)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-21T20:19:19Z
- **提交信息**: [CI] Fix MultiConnector accuracy test lifecycle (#53023)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [29b7c2f](https://github.com/vllm-project/vllm/commit/29b7c2f7d41f326a8d7227c710d2e1ffe79668d6)

- **作者**: Divakar Verma
- **时间**: 2026-08-21T20:17:34Z
- **提交信息**: [ROCm][CI] aiter kernel ops - enable rope test (#52854)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [a0af854](https://github.com/vllm-project/vllm/commit/a0af854f5d9647637a1f8c9ab9edd3722fe9956c)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-21T20:17:18Z
- **提交信息**: [ROCm][CI] Stabilize MI355 FlyDSL MoE accuracy test (#53024)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [b5f7fcc](https://github.com/vllm-project/vllm/commit/b5f7fcc79df9ecde8edd7e4a4354b1ee47d79ec3)

- **作者**: Divakar Verma
- **时间**: 2026-08-21T20:16:45Z
- **提交信息**: [ROCm][CI] Add float16 dtype and unsupported head size tests for paged attention (#53177)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [88eb946](https://github.com/vllm-project/vllm/commit/88eb946cb1a0901bcbb842de463d6c1cae035fa9)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-21T20:15:25Z
- **提交信息**: [ROCm][CI] Stabilize MI355 FusedMoE test group (#53025)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [c0ff334](https://github.com/vllm-project/vllm/commit/c0ff33404b93d82f2f2f30a362f372fc99eca8f7)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-21T20:08:13Z
- **提交信息**: Revert compile-cache device index regression on CPU (#53304)

### [f15ea66](https://github.com/vllm-project/vllm/commit/f15ea66b3006ac3b6ea1571248c07f7b35916dd2)

- **作者**: djramic
- **时间**: 2026-08-21T20:06:19Z
- **提交信息**: [ROCm][Test] Use platform FP8 dtype in ModelOpt FP8_PB_WO test (#53268)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [e6f35d3](https://github.com/vllm-project/vllm/commit/e6f35d3c69b23b2ed35afebde31a0567c40bc661)

- **作者**: Wentao Ye
- **时间**: 2026-08-21T19:11:45Z
- **提交信息**: [DSv4 Perf] Adaptive topk width for dsv4, making #50004 back (#52823)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d6c2fec](https://github.com/vllm-project/vllm/commit/d6c2fec9fd72eeac44f42c884e19a1c6bd1142a7)

- **作者**: Summer Yang
- **时间**: 2026-08-21T18:42:52Z
- **提交信息**: [Cleanup][MLA] Remove FlashInfer DSpark DCP support (#53139)

Signed-off-by: Summer Yang <girasoleyang@gmail.com>

### [d9e0ace](https://github.com/vllm-project/vllm/commit/d9e0ace7a07d38095d8b34bad58852cdffa27744)

- **作者**: Stefano Castagnetta
- **时间**: 2026-08-21T18:41:24Z
- **提交信息**: [Bugfix][Attention] Fall back to native FlashInfer decode when XQA cannot serve a KV-cache group's head_dim (#53111)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ba53da6](https://github.com/vllm-project/vllm/commit/ba53da60bb1aeec200d05101936a5474ee46c4eb)

- **作者**: vllm-agent
- **时间**: 2026-08-21T18:39:28Z
- **提交信息**: Revert "[Bugfix][MoE] Tune FlashInfer experts to scheduler token limit" (#52989) (#53186)

Co-authored-by: vllm-ci-failure-analyzer <kevin@inferact.ai>

### [7a2fdba](https://github.com/vllm-project/vllm/commit/7a2fdbaac44921f57b04e53d6f49ed594c2209b6)

- **作者**: Wentao Ye
- **时间**: 2026-08-21T17:29:59Z
- **提交信息**: [K3 Perf] Fuse MXFP4 top-k finalization into latent-tail, ~5% E2E latency reduction (#53152)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [fe76112](https://github.com/vllm-project/vllm/commit/fe76112ff2981e9373765d76687d53f94880f38e)

- **作者**: Fangzhou Ai
- **时间**: 2026-08-21T17:00:39Z
- **提交信息**: [ROCm][Perf] Optimize DeepSeek V4 C4A top-k with AITER (#52882)

### [1baf372](https://github.com/vllm-project/vllm/commit/1baf372bfc14d739860b4a7122877e22ef0dcbf1)

- **作者**: Tan Chao
- **时间**: 2026-08-21T16:07:24Z
- **提交信息**: [Frontend] Use VLLMValidationError for batch request URL validation (#50191)

Signed-off-by: Chao Tan <chaos.tc@gmail.com>

### [47cd1c8](https://github.com/vllm-project/vllm/commit/47cd1c8885b79be4ea92bae8574a07e7b60f8a23)

- **作者**: Frederik Gossen
- **时间**: 2026-08-21T16:07:21Z
- **提交信息**: [Core] Add dynamo_timed tracing for print_readable (#40834)

Signed-off-by: Frederik Gossen <frgossen@meta.com>

### [e00a034](https://github.com/vllm-project/vllm/commit/e00a034ad1d7c8ccce28f135fa9380dd9110e525)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-08-21T16:07:19Z
- **提交信息**: (security) fix: enforce decoder prompt-length validation for skip-che… (#46588)

Signed-off-by: jperezde <jperezde@redhat.com>

### [b41dc4e](https://github.com/vllm-project/vllm/commit/b41dc4ec722a70b141696e75ff04c7016eb5ed15)

- **作者**: Wei-Cheng (Wayne) Chiu
- **时间**: 2026-08-21T16:07:17Z
- **提交信息**: [Bugfix] Return HTTP 500 for non-streaming generate errors (#49195)

Signed-off-by: WEI CHENG CHIU <waynehacking8@gmail.com>

### [6dcc5d7](https://github.com/vllm-project/vllm/commit/6dcc5d7caeffa7f69239153b171249e867ca6050)

- **作者**: Neil Schemenauer
- **时间**: 2026-08-21T16:07:16Z
- **提交信息**: [Bugfix] Include device index in compile cache paths (#38962)

Signed-off-by: Neil Schemenauer <nas@arctrix.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [463aa5e](https://github.com/vllm-project/vllm/commit/463aa5e30fe0b51a5d6ef22897962fc1be97cb85)

- **作者**: kliuae
- **时间**: 2026-08-21T16:07:13Z
- **提交信息**: [ROCm][Perf] Kimi-K3 Fused kernels for KDA prefill (#52606)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [d53b1c2](https://github.com/vllm-project/vllm/commit/d53b1c2efc0ca7161c3844f51ca9acbcdb7129d5)

- **作者**: Tiezhen WANG
- **时间**: 2026-08-21T16:07:10Z
- **提交信息**: Remove native Hunyuan V1 and VL implementations (#53272)

Signed-off-by: Xianbao QIAN <xianbao.qian@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [27ec8ac](https://github.com/vllm-project/vllm/commit/27ec8ac626345498fdac0527a4fcd1451c24bebc)

- **作者**: SoluMilken
- **时间**: 2026-08-21T16:07:08Z
- **提交信息**: [Bugfix] Fix MTP draft model using local cache path instead of S3 URL with runai_streamer (#42079)

Signed-off-by: SoluMilken <ypiheyn.imm02g@g2.nctu.edu.tw>

### [72aedcc](https://github.com/vllm-project/vllm/commit/72aedcc426c23efe01e2484cadb76074330a10a9)

- **作者**: Lucas Wilkinson
- **时间**: 2026-08-21T16:07:05Z
- **提交信息**: [DCP] Default query replication for GLM sparse attention (#50382)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [cd7b7c2](https://github.com/vllm-project/vllm/commit/cd7b7c265a30b8c3e5c908d59f4cb0d7dd8f8ff3)

- **作者**: Hongxia Yang
- **时间**: 2026-08-21T16:07:03Z
- **提交信息**: [ROCm] Cpu offload for ROCm 7.13+ to align the hipMemcpyBatchAsync params and perf in 7.14x (#43018)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [c1d7a38](https://github.com/vllm-project/vllm/commit/c1d7a3808d28dd6e378785852acdccaab3553c39)

- **作者**: DCo
- **时间**: 2026-08-21T16:07:01Z
- **提交信息**: [Bugfix] Fix HYV3 shared_mlp prefix for compressed-tensors ignore matching (#48682)

Signed-off-by: Xiaoyi Xu <xu_xiaoyi@hotmail.com>

### [1183f04](https://github.com/vllm-project/vllm/commit/1183f04b74b1a0b6db91ae992ebbc1ea89050cac)

- **作者**: Morrison Turnansky
- **时间**: 2026-08-21T16:06:59Z
- **提交信息**: [Bugfix] test_batch_inference_correctness now uses batch invariance (#48040)

Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [fbb17e7](https://github.com/vllm-project/vllm/commit/fbb17e780b1b6e91b3eb9777eb44d3288c2c30b6)

- **作者**: ErenAta16
- **时间**: 2026-08-21T16:06:56Z
- **提交信息**: [Bugfix] Fix six quantization exception messages split across positional args (#50479)

Signed-off-by: ErenAta16 <erena6466@gmail.com>

### [18aa245](https://github.com/vllm-project/vllm/commit/18aa245a99d82c5ef35281c36787accd26effd8f)

- **作者**: Greg Pereira
- **时间**: 2026-08-21T16:06:54Z
- **提交信息**: using existing uvicorn configuration for dp supervisor (#52473)

Signed-off-by: Gregory Pereira <grpereir@redhat.com>

### [08b73d0](https://github.com/vllm-project/vllm/commit/08b73d07cc467ea29f5f13f2eec067231c7e7322)

- **作者**: Bugen Zhao
- **时间**: 2026-08-21T16:06:52Z
- **提交信息**: [Frontend] Prevent Kimi K3 reserved markers in response text (#52889)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [6d8cd88](https://github.com/vllm-project/vllm/commit/6d8cd88e8d7b5baa8456195b1298be670f8fe2d1)

- **作者**: Russell Bryant
- **时间**: 2026-08-21T16:06:49Z
- **提交信息**: [Docs] document cache salting for prefix cache timing side-channel mitigation (#39082)

Signed-off-by: Russell Bryant <rbryant@redhat.com>

### [6f74337](https://github.com/vllm-project/vllm/commit/6f74337c4748e8a84c9552b1d6040eb7b58f9c4b)

- **作者**: Lee Yongjun
- **时间**: 2026-08-21T16:06:47Z
- **提交信息**: [Bugfix][Spec Decode]Preserve user --speculative-config overrides for speculators-format models (#42376)

Signed-off-by: leeyongjun <jqueen.astro@gmail.com>
Signed-off-by: Lee Yongjun <35302114+elwhyjay@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [574e6a0](https://github.com/vllm-project/vllm/commit/574e6a00efd3d594c4d7f72e766c3e605316a118)

- **作者**: yimdev
- **时间**: 2026-08-21T15:31:14Z
- **提交信息**: [Bugfix][Attention] Normalize FlashInfer prefill LSE before merging (#52796)

Signed-off-by: yimdev <5779256+yimdev@users.noreply.github.com>
Co-authored-by: usberkeley <150880684+usberkeley@users.noreply.github.com>

### [2740c81](https://github.com/vllm-project/vllm/commit/2740c817ffbe6c1980507c7cbd27b4bc94d2c856)

- **作者**: Luke Alonso
- **时间**: 2026-08-21T15:04:36Z
- **提交信息**: [Kernel] Add b12x FP4 MoE backend (#52018)

Signed-off-by: Luke Alonso <lalonso@gmail.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Signed-off-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [5ee84d3](https://github.com/vllm-project/vllm/commit/5ee84d3c5207bd59faa53e19e60fa82e34961444)

- **作者**: Frederik Gossen
- **时间**: 2026-08-21T14:14:52Z
- **提交信息**: [CI][Bugfix] Use a prompt that survives offload-resume rounding in mamba offload test (#53146)

Signed-off-by: Frederik Gossen <frgossen@meta.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [cda3868](https://github.com/vllm-project/vllm/commit/cda3868f5dd83f413be978148ad8bb63c1f57c70)

- **作者**: shijuzhao
- **时间**: 2026-08-21T13:41:31Z
- **提交信息**: [Bugfix] Deterministic MoE combine (reduce_scatterv) under VLLM_BATCH_INVARIANT (#45683)

Signed-off-by: shijuzhao <shijuzhao@tencent.com>
Co-authored-by: shijuzhao <shijuzhao@tencent.com>

### [c8438a3](https://github.com/vllm-project/vllm/commit/c8438a3d40168ce1d9eade0dc15ccbe5d27adb68)

- **作者**: Harish Gaikwad
- **时间**: 2026-08-21T12:03:41Z
- **提交信息**: [Doc] Fix dead link in KV transfer README (#53230)

Signed-off-by: hagaikwa-redhat <hagaikwa@redhat.com>

### [a60c66e](https://github.com/vllm-project/vllm/commit/a60c66e3dcd563a293a9a3f54541e7405e95c82e)

- **作者**: Shuai Shao
- **时间**: 2026-08-21T10:37:06Z
- **提交信息**: [Bugfix] Fix int32 index overflow in LoRA punica kernels at long context (#53034)

Signed-off-by: Shuai Shao <ss@rungalileo.io>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [6feafb8](https://github.com/vllm-project/vllm/commit/6feafb8b7d9c5b21ab747279182c820ef2d9265e)

- **作者**: Yan Ma
- **时间**: 2026-08-21T10:13:27Z
- **提交信息**: [XPU] follow cuda path for mrope on XPU (#53201)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [e85d1b6](https://github.com/vllm-project/vllm/commit/e85d1b69cf2f1c6101cfc7c799bb0c457cacc4b3)

- **作者**: linitra24
- **时间**: 2026-08-21T09:45:54Z
- **提交信息**: [Bugfix][LoRA] Use an explicit capability flag for tower connector LoRA (#53092)

Signed-off-by: linitra24 <Joy25810@foxmail.com>

### [36bad1b](https://github.com/vllm-project/vllm/commit/36bad1b90cb2958b6de4abdb5a9249b136f39720)

- **作者**: xiangdong
- **时间**: 2026-08-21T09:31:25Z
- **提交信息**: [XPU][CI]Add more cases in intel GPU CI and reorganize to align non-xpu part (#51630)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [0a21947](https://github.com/vllm-project/vllm/commit/0a21947d710f5aedb1865038ebef20e141b29c58)

- **作者**: xiangdong
- **时间**: 2026-08-21T08:02:34Z
- **提交信息**: [XPU][CI]Add parallelism for long-running Intel GPU cases (#52257)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-22
**监控日期**: 2026-08-21
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6224
- **最后更新**: 2026-08-21T21:41:01Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: 汪志鹏, R0CKSTAR, Nick Cao

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交以 **Bug修复** 为主（4项），辅以 **文档更新**（1项）和 **开发流程优化**（1项）。无新增功能或性能优化类提交。

### 2. 关键变更点与项目方向的关系
- **Step-Audio2 依赖修复**：移除被意外重新引入的 `librosa` 依赖，维护了音频模型服务的依赖纯净性，符合项目“易用、快速、低成本”的定位。
- **CosyVoice3 STFT 设备不匹配修复**：解决音频处理中张量设备（CPU/GPU）不一致问题，直接提升多模态推理的稳定性。
- **MiniMax-H3 CPU 卸载修复**：修复扩散模型在模型级 CPU 卸载时的驻留问题，优化了显存管理，契合项目“低成本”服务目标。
- **MiniCPM-o 异步分块修复**：修复快照替换和提示词清理逻辑，增强长序列处理时的内存安全与并发稳定性。
- **Star History 图表恢复**：文档维护，提升项目展示效果。
- **新增简化审查技能**：为仓库引入代码审查自动化技能，属于开发流程改进。

### 3. 对项目的影响与潜在意义
- 修复覆盖 **音频（Step-Audio2、CosyVoice3）、扩散模型（MiniMax-H3）、多模态（MiniCPM-o）** 三大核心方向，表明项目正在快速迭代中加固各模态的可靠性。
- 设备不匹配和 CPU 卸载问题直接影响实际部署体验，修复后能显著降低用户在多 GPU/混合设备环境下的使用门槛。
- 异步分块修复对长音频/视频输入场景至关重要，为后续支持更复杂的 omni-modality 任务打下基础。

### 4. 值得关注的技术点
- **STFT 设备一致性**：涉及音频特征提取在异构设备间的正确性，是音频模型服务中的常见隐患。
- **模型级 CPU 卸载**：MiniMax-H3 的修复表明项目在显存优化上采用了细粒度的驻留控制，值得关注其实现方式。
- **异步分块快照机制**：MiniCPM-o 的修复涉及并发场景下的状态管理，对多请求服务架构有参考价值。

### 5. 对项目发展的影响
结合 README 中“**为所有人提供简单、快速、便宜的 omni-modality 模型服务**”的愿景，本次提交虽无新功能，但通过系统性修复音频、扩散、多模态三大方向的稳定性问题，**夯实了项目作为统一多模态服务框架的基础**。特别是对设备兼容性和显存管理的优化，直接服务于“低成本”目标，有助于吸引更广泛的用户群体。开发流程上引入审查技能，也体现了项目在规模化协作中对代码质量的重视。整体而言，这是一次**以稳定性换信任**的扎实迭代，为后续功能扩展提供了更可靠的地基。

## 详细提交记录

### [cfbf139](https://github.com/vllm-project/vllm-omni/commit/cfbf1392c5b97c81d0189a60f54b2798e7935401)

- **作者**: Nick Cao
- **时间**: 2026-08-21T21:33:07Z
- **提交信息**: [Bugfix] Drop librosa reintroduced by Step-Audio2 (#6467)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [dc72559](https://github.com/vllm-project/vllm-omni/commit/dc72559d5d975e4ba2f60461455d6b3cfeac7102)

- **作者**: 汪志鹏
- **时间**: 2026-08-21T11:45:46Z
- **提交信息**: [BugFix]: CosyVoice3 STFT window device mismatch (#6454)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [260db8b](https://github.com/vllm-project/vllm-omni/commit/260db8bab5443f52b38b8eb813899a076c18d54c)

- **作者**: R0CKSTAR
- **时间**: 2026-08-21T10:30:53Z
- **提交信息**: [Bugfix][Diffusion] Fix MiniMax-H3 model-level CPU offload residency (#6072)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [4f7c08c](https://github.com/vllm-project/vllm-omni/commit/4f7c08c0eb0dd2dd47a1baa70384a46c7536afd5)

- **作者**: NATURE
- **时间**: 2026-08-21T08:37:21Z
- **提交信息**: [Bugfix][MiniCPM-o] Fix async-chunk snapshot replacement and prompt cleanup (#6406)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [ea0a244](https://github.com/vllm-project/vllm-omni/commit/ea0a24465b6ee2d01c87c9b035fa6bc147151b0f)

- **作者**: Alicia
- **时间**: 2026-08-21T08:35:03Z
- **提交信息**: [Docs] Restore the Star History chart (#6446)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [fc163cd](https://github.com/vllm-project/vllm-omni/commit/fc163cd90f71746c7df112c67b0f3620d7a90ee5)

- **作者**: 汪志鹏
- **时间**: 2026-08-21T07:31:42Z
- **提交信息**: [Skills] Add vLLM-Omni simplification review skill (#6363)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>

---
