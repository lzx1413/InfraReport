# GitHub Stars 合并报告 - 2026-10-12

**合并日期**: 2026-10-13
**监控日期**: 2026-10-12
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


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2236
- **最后更新**: 2026-10-12T11:45:57Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

## 提交分析：[57e5f6d] stream per-expert Qwen3-Omni-MoE and DeepSeek-V3 checkpoints under EP

### 1. 主要更新类型
**功能新增（feat）**：为专家并行（Expert Parallelism, EP）场景下的模型检查点提供按专家（per-expert）流式加载能力。

### 2. 关键变更点及与项目方向的关系
- 针对 **Qwen3-Omni-MoE** 和 **DeepSeek-V3** 两个代表性 MoE 模型，实现检查点的流式（stream）与按专家切分加载。
- VeOmni 的核心定位是"以模型为中心的分布式训练配方库（Model-Centric Distributed Recipe Zoo）"，覆盖任意模态的规模化训练。MoE 模型参数量巨大（DeepSeek-V3 达 671B），在 EP 并行下需要把专家分片分布在多个设备上，传统的整体加载方式会导致内存峰值过高、加载缓慢。
- 该提交将"分片/流式加载"这一分布式基础设施能力补全到两大旗舰 MoE 模型上，属于其分布式训练 recipe 的关键一环。

### 3. 对项目的影响和潜在意义
- **降低大模型训练门槛**：用户无需在单机或统一内存中持有完整权重，可在 EP 并行下高效加载万亿级 MoE 模型，显著减少显存/内存占用和启动时间。
- **强化对前沿模型的支持**：Qwen3-Omni-Moe 是字节/阿里生态中多模态 Omni 方向的代表，DeepSeek-V3 是 MoE 架构的标杆，支持两者表明 VeOmni 正成为 MoE 大规模训练的通用底座。
- **提升可用性与可扩展性**：流式加载使训练可从受限硬件扩展到大规模集群，与项目"Scaling Any Modality Model Training"的目标高度一致。

### 4. 值得关注的技术点
- **per-expert 流式加载**：需要与 EP 的专家分片布局严格对齐，避免重复读取或读取遗漏，涉及 checkpoint 格式设计（如 safetensors 分片元数据）与分发逻辑。
- **多模型泛化**：同一套流式机制能否覆盖不同 MoE 架构（Qwen3-Omni-MoE 的注意力/多模态塔 vs DeepSeek-V3 的 MLA + MoE），体现框架的抽象能力。
- **协作者为 Cursor**：由 AI 编程助手协作完成，反映出该项目在工程实践中已引入 AI 辅助开发流程，值得关注其代码审查与质量管控方式。

### 5. 对项目发展的整体影响
结合 README 可知，VeOmni 旨在提供覆盖多模态、可扩展的分布式训练配方。此次提交补全了 MoE + EP 场景下的检查点加载链路，使项目从"支持 MoE 训练"迈向"支持万亿级 MoE 的工程化落地"，是其配方库从功能覆盖走向生产可用的重要一步。这将吸引更多需要训练或微调 Qwen3-Omni、DeepSeek-V3 类模型的研究者与工程师，巩固 VeOmni 在开源分布式训练框架中的差异化定位。

## 详细提交记录

### [57e5f6d](https://github.com/ByteDance-Seed/VeOmni/commit/57e5f6d392a230c31488f57542cd534e1c73ed33)

- **作者**: Coach257
- **时间**: 2026-10-12T11:45:51Z
- **提交信息**: [model] feat: stream per-expert Qwen3-Omni-MoE and DeepSeek-V3 checkpoints under EP (#1274)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2897
- **最后更新**: 2026-10-13T01:41:16Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 3
- **主要提交者**: Bilang ZHANG, Yang Yong (雍洋), Chengtao Lv

## AI分析总结

# LightX2V 昨日提交分析

## 1. 主要更新类型

本批次提交涵盖**功能新增**（量化支持、APP发布）、**重构**（配置加载简化）和**文档更新**（三次README修订），整体以功能推进为主。

## 2. 关键变更点及与项目方向的关系

- **RealtimeWan 量化支持（#1603、#1605）**：核心变更在于为 RealtimeWan 实时视频生成模型添加了量化支持，包括在线（#1603）和离线（#1605）两种量化路径。这直接契合 LightX2V "轻量级视频生成推理" 的核心定位——通过量化降低显存占用和加速推理，使实时视频生成更加可行。

- **LightX2V APP 发布（#1608）**：标志着项目从纯推理框架向产品化/应用化迈出一步，提供更友好的用户界面或部署形态，降低使用门槛。

- **配置加载重构（#1604）**：简化了配置文件的加载逻辑，并同步精简了 Wan 和 MiniMax-H3 的示例。这是技术债务清理，使代码更易维护、示例更直观。

## 3. 对项目的影响和潜在意义

- **实时性提升**：量化是实现 RealtimeWan 实时推理的关键技术手段，离线量化进一步提升了部署灵活性，使用户可以在推理前预先优化模型，减少运行时开销。
- **生态扩展**：APP 的发布表明项目正在从研究/实验阶段向实际应用拓展，有望吸引非技术背景的用户群体。
- **维护性改善**：配置重构降低了新用户上手和贡献者扩展新模型的门槛，有助于社区发展。

## 4. 值得关注的技术点

- **在线与离线量化的协同设计**：项目同时支持运行时量化和预处理量化，这种双路径设计为不同部署场景提供了灵活性。
- **RealtimeWan 定位**：Wan 系列模型在视频生成领域表现突出，针对其的实时化优化是前沿方向，量化策略的选择（如权重量化 vs 激活量化）对质量-速度权衡至关重要。
- **多模型支持的配置架构**：对 Wan 和 MiniMax-H3 示例的简化反映了项目对多模型架构支持的持续优化。

## 5. 对项目发展的影响

结合 README 中 LightX2V 作为"轻量级视频生成推理框架"的定位，本批次提交体现了清晰的演进路径：**从核心推理优化（量化）→ 工程质量提升（重构）→ 产品化输出（APP发布）**。这三步使得项目既能保持技术前沿性（实时视频生成），又在易用性和可维护性上持续改善，为构建完整的视频生成推理生态奠定了基础。持续的 README 更新也表明项目正在积极完善对外文档，配合新功能的发布。

## 详细提交记录

### [5fe46a8](https://github.com/ModelTC/LightX2V/commit/5fe46a85493cae7552bc493fe0d5c2b4c04bc730)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-12T22:41:09Z
- **提交信息**: update readme (#1611)

### [7d446dd](https://github.com/ModelTC/LightX2V/commit/7d446ddfaa7233ab2ea7036fe4378df98a483c0c)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-12T22:29:51Z
- **提交信息**: update readme (#1610)

### [b83d3df](https://github.com/ModelTC/LightX2V/commit/b83d3dff0cc8a31f267714bc84050f27d245731a)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-12T22:26:17Z
- **提交信息**: update readme (#1609)

### [ec29400](https://github.com/ModelTC/LightX2V/commit/ec29400c50d3ee4f451b94457d39e3783076529b)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-12T22:20:57Z
- **提交信息**: Released LightX2V APP (#1608)

### [24ed42e](https://github.com/ModelTC/LightX2V/commit/24ed42effe8cf38228e073599114dc67c77c0025)

- **作者**: Chengtao Lv
- **时间**: 2026-10-12T16:24:35Z
- **提交信息**: update offline quantization for realtimewam (#1605)

### [c301bc5](https://github.com/ModelTC/LightX2V/commit/c301bc5de71aaeca12ff2a8ae3e4116e1ee8e3bb)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-12T11:06:15Z
- **提交信息**: refactor: simplify config loading and Wan/MiniMax-H3 examples (#1604)

### [94f0f19](https://github.com/ModelTC/LightX2V/commit/94f0f19459e66f61a723db7690f1707f308599ef)

- **作者**: Chengtao Lv
- **时间**: 2026-10-12T07:21:55Z
- **提交信息**: support quantization for realtimewam (#1603)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2293
- **最后更新**: 2026-10-12T08:45:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6600
- **最后更新**: 2026-10-13T02:59:23Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 7
- **主要提交者**: Fabio, Ka-Hyun Nam, Anerudhan Gopal

## AI分析总结

# FlashInfer 昨日提交合并分析（共 10 个提交）

## 1. 主要更新类型
- **性能优化**（约 6 条）：NVFP4/MXFP8 GEMM、SwiGLU/QKV epilogue 的 TMEM overlap、Cake 注意力调度、SM107a（Rubin）去除 FP64 指令等。
- **Bug 修复**（3 条）：MoE workspace 偏移竞争、KDA 推理张量元数据缓存、多后端权重准备。
- **CI/基础设施**（1 条）：多 GPU/多节点测试路径过滤。

## 2. 关键变更点与项目方向
FlashInfer 定位于"高性能 GPU 推理内核"，本日工作紧密围绕三条主线：

**Blackwell 低精度计算深化**：两条 TMEM overlap 提交（#6255、#6286）将累加器双缓冲扩展到 NVFP4 SwiGLU 和 QKV+QKNorm+RoPE epilogue，实现 1.34x–1.60x 加速；warp 级 split-K MXFP8 GEMM（#6167）在小 M 形状上最高提升 1.8x。TMEM overlap 通过寄存器保留首个子块，使 QKNorm 全头归一化与流水线并存，且保持 bitwise 一致。

**Rubin（SM107a）前瞻性适配**：Cake GDN 解码内核将 FP64 缩放替换为自定义的 `cake_f32_mul_f64const_rn` 辅助函数，正常路径完全避免 FP64 乘法，异常输入（次正规数/NaN/无穷）保留 `__noinline__` FP64 参考实现兜底，保证逐位一致。多架构记录机制让 SM100a/SM103a 内核文本逐字节不变，SM107a 视图复用同一符号与 host shim。fp32 T=1 pretranspose 按 state head 数（阈值 256）动态选择 `splitv8`/`tilev32` 变体，仅改变 CTA 映射，输出位等价。

**MoE 与多后端正确性**：#6376 修复 one-sided MoE workspace 中因 NVFP4/BF16 交替布局导致的跨 rank 竞态——仅将 combine 区域固定到末尾对齐偏移，不改变分配大小与内核同步，属最小侵入修复；#6142 确保 CuTe 与 TRT-LLM 双后端权重完整准备；#6372 修复 vLLM CI 报告的崩溃；KDA 修复区分 inference tensor 的版本计数语义，兼顾 CUDA graph 复用。

**调度与内核多样性**：Cake 注意力 round-13（#6375）引入动态 ticket 调度与 publish-tail cut，生成 3 个新程序（共 11 个），按 plan 动态选择 DYN_SCHED/SREAD/静态三种位等价程序；MLA KV 量化 FP8（#5667）按头数自动路由 specialized/Cake 双后端，体现"按形状选最优实现"的 autotuning 哲学。

## 3. 对项目的影响
- **Rubin 先发优势**：FP64 在推理 GPU 上吞吐极低，去除后显著提升 SM107a 解码性能，为新硬件上市即提供最优性能打下基础。
- **生产可靠性**：多后端、分片 EP 场景的竞态与缓存修复，直接增强 vLLM、SGLang 等下游框架集成的稳定性。
- **工程化成熟度**："一条记录、多架构输出"机制降低多架构维护成本，避免 shim 代码复制粘贴；GB200/GB300 实测基准数据增强结果可信度。
- **贡献流程加速**：CI 支持 `/bot run` 路径过滤，减少无关测试开销。

## 4. 值得关注的技术点
- 内容寻址管理的 device helper 文件（`csrc/cake_device_helpers/`），利于编译缓存命中与版本追踪。
- 冷热路径分离：FP64 版本外置为 `__noinline__` 函数，仅异常输入触发。
- 动态 grid 推导与 shim 自校验，开发阶段即可暴露配置错误。
- 全线强调 bit-for-bit 一致性，把数值正确性作为硬性约束，保障 LLM 推理结果可复现。

## 5. 整体展望
这些工作共同推动 FlashInfer 在 Blackwell 建立低精度性能护城河、在 Rubin 完成前瞻布局，并通过多后端路由与正确性修复，从"单点优化的内核集合"演进为"可持续维护的多架构内核平台"，强化其作为推理引擎核心加速库的竞争力。

## 详细提交记录

### [5f8c9ef](https://github.com/flashinfer-ai/flashinfer/commit/5f8c9efd7feedaae580f2cc02733555de50f920f)

- **作者**: Anerudhan Gopal
- **时间**: 2026-10-12T23:20:49Z
- **提交信息**: fix: keep one-sided MoE combine workspace offset stable (#6376)

<!-- .github/pull_request_template.md -->

## 📌 Description

Alternating NVFP4 and BF16 dispatch payloads moves the combine offset in
a shared one-sided MoE workspace. A fast rank can then overwrite combine
data that another rank still reads. Changes in the runtime token count
can cause the same overlap.

Reserve an aligned combine region at a fixed offset at the end of the
shared workspace. Reuse that offset for staging and direct workspace
output. Check dispatch bounds before launching GPU writes. This keeps
the allocation size and kernel synchronization unchanged.

## 🔍 Related Issues

Fixes #6069

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
- [x] All tests are passing (`unittest`, etc.).

Tested the TRT-LLM backend on four GB200 GPUs and four GB300 GPUs on
Lyris:

| GPU | New regression, before | New regression, after | Existing MPI
tests | Host tests |
| --- | --- | --- | --- | --- |
| GB200 | 6 failed, 2 passed | 8 passed | 17 passed | 14 passed |
| GB300 | 6 failed, 2 passed | 8 passed | 17 passed | 14 passed |

The regression alternates NVFP4-layout and BF16 payloads across two
objects sharing one workspace. It covers eager execution, graph replay,
direct workspace output, low-precision combine, uneven and empty ranks,
and changing token counts. Each case checks 20 repetitions of six
rounds, with hidden size 6144, top-k 8, and capacity 32768 tokens per
rank.

```sh
mpirun -np 4 python -m pytest tests/comm/test_mnnvl_moe_alltoall.py -q
python -m pytest tests/comm/test_moe_a2a_workspace.py tests/comm/test_moe_a2a_recv_view_cache.py -q
```

Host tests comprise 10 new bounds/layout tests and four existing
receive-view-cache tests. Environment: PyTorch 2.12.0+cu130, CUDA 13.0,
Open MPI 4.1.6, mpi4py 4.1.2. Drivers: GB200 580.196; GB300 580.173.10.

### Microbenchmark

Dispatch plus combine, with no expert GEMM or quantization computation.
Four ranks, hidden size 6144, top-k 8, BF16 combine, capacity 4096.
NVFP4 denotes packed-data and scale payload shapes. CUDA events measure
graph replay through `bench_gpu_time`: 10 warmup replays, 50 measured
replays, 10 calls per graph, reused buffers. Each value is the median of
the maximum rank time per sample.

| GPU | Tokens/rank | Dispatch | Before (µs) | After (µs) |
| --- | ---: | --- | ---: | ---: |
| GB200 | 32 | NVFP4 | 27.024 | 27.024 |
| GB200 | 32 | BF16 | 27.741 | 27.642 |
| GB200 | 256 | NVFP4 | 36.240 | 36.325 |
| GB200 | 256 | BF16 | 46.070 | 46.170 |
| GB200 | 4096 | NVFP4 | 423.598 | 422.907 |
| GB200 | 4096 | BF16 | 577.426 | 576.701 |
| GB300 | 32 | NVFP4 | 26.626 | 26.797 |
| GB300 | 32 | BF16 | 27.386 | 27.235 |
| GB300 | 256 | NVFP4 | 35.837 | 35.853 |
| GB300 | 256 | BF16 | 45.822 | 45.872 |
| GB300 | 4096 | NVFP4 | 417.378 | 416.963 |
| GB300 | 4096 | BF16 | 570.309 | 570.360 |

All observed changes are within 0.65%; these runs do not establish a
speedup.

<details>
<summary>Reproduce the microbenchmark</summary>

Save the script below as `bench_moe_a2a_6069.py`. Run it against base
commit `85ec446e2ef04bcbae819779ee169ac01a33c365` and this PR, using the
same environment:

```sh
VARIANT=before mpirun -np 4 python bench_moe_a2a_6069.py
# Repeat from the PR checkout with VARIANT=after.
```

```python
"""MPI microbenchmark: dispatch plus combine, without expert computation."""
import json
import os
import statistics

import torch
from mpi4py import MPI
from flashinfer.comm import MoeAlltoAll
from flashinfer.comm.mapping import Mapping
from flashinfer.testing import bench_gpu_time

comm = MPI.COMM_WORLD
rank, ep_size = comm.Get_rank(), comm.Get_size()
local = comm.Split_type(MPI.COMM_TYPE_SHARED)
torch.cuda.set_device(local.Get_rank())
mapping = Mapping(rank=rank, world_size=ep_size, tp_size=ep_size,
                  moe_ep_size=ep_size, gpus_per_node=local.Get_size())
hidden, top_k, capacity = 6144, 8, 4096
for tokens in (32, 256, 4096):
    for quantized in (True, False):
        a2a = MoeAlltoAll(mapping, capacity, top_k, 256, hidden_size=hidden)
        ids = torch.arange(top_k, device='cuda', dtype=torch.int32)
        ids = ((ids % ep_size) * (256 // ep_size) + ids // ep_size).repeat(tokens, 1)
        if quantized:
            payloads = [torch.ones((tokens, hidden // 2), dtype=torch.uint8, device='cuda'),
                        torch.ones((tokens, hidden // 16), dtype=torch.uint8, device='cuda')]
        else:
            payloads = [torch.ones((tokens, hidden), dtype=torch.bfloat16, device='cuda')]
        payloads += [ids, torch.full((tokens, top_k), 0.125, device='cuda')]
        expert = torch.full((ep_size, tokens, hidden), rank + 1,
                            dtype=torch.bfloat16, device='cuda')
        output = torch.empty((tokens, hidden), dtype=torch.bfloat16, device='cuda')

        def run():
            a2a.dispatch(ids, payloads, tokens)
            a2a.combine(expert, tokens, output=output)

        for _ in range(5):
            run()
        torch.cuda.synchronize()
        assert output.eq(ep_size * (ep_size + 1) // 2).all().item()
        comm.Barrier()
        times = bench_gpu_time(run, dry_run_iters=10, repeat_iters=50,
                               use_cuda_graph=True, num_iters_within_graph=10,
                               cold_l2_cache=False, enable_cupti=False)
        samples = comm.allgather(times)
        slowest = [max(x) for x in zip(*samples)]
        if rank == 0:
            print('BENCH ' + json.dumps({
                'variant': os.environ['VARIANT'], 'gpu': torch.cuda.get_device_name(),
                'ep_size': ep_size, 'tokens': tokens, 'hidden': hidden,
                'dispatch': 'nvfp4' if quantized else 'bf16',
                'median_us': statistics.median(slowest) * 1000,
                'min_us': min(slowest) * 1000, 'max_us': max(slowest) * 1000,
                'samples_us': [v * 1000 for v in slowest],
            }), flush=True)
        comm.Barrier()
        a2a._reset_workspace()
```

</details>

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

- Public signatures are unchanged. Shared workspace users must keep the
combine hidden size and dtype width fixed; changes now raise
`ValueError`. Dispatches that exceed the reserved region fail before
launch. Callers must size the workspace for their largest dispatch
payload.
- Tests cover communication on four ranks. The full eight-rank GLM
deployment and speculative-token acceptance rates were not tested.
- Graph timings exclude the new CPU checks during eager execution and
capture.
- Pre-commit checks passed and were scoped to the three changed files,
as the self-review guide recommends. The `--all-files` checkbox remains
unchecked.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability when alternating communication operations that
share workspace, preserving correct combined results across repeated
dispatches.
* Added safeguards for token limits and workspace capacity to prevent
invalid or overlapping operations.
* Stabilized combine storage placement across dispatch payload shapes
and formats.
* Improved coverage for graph-captured operations and low-precision
combine scenarios.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1ed137d](https://github.com/flashinfer-ai/flashinfer/commit/1ed137d9f8283e55c4388782cde4b54eeabad2ea)

- **作者**: eigen
- **时间**: 2026-10-12T22:50:16Z
- **提交信息**: perf(cake_minimax_h3_varlen_attention): round-13 per-plan program dispatch -- dynamic ticket scheduling for long multi-wave plans (SM100a, SM103a) and a publish-tail cut for the SM100a static plans (#6375)

## Summary

`flashinfer.experimental.minimax_h3_varlen_attention` (Cake backend,
SM100a/SM103a BF16 packed-varlen attention), round 13 on top of #6328.
The host planner now selects one of three bitwise-identical programs per
plan:

- **Dynamic whole-unit ticket scheduling** (`DYN_SCHED` + ticket
prefetch) for plans with >= 2 waves, >= 8192 stage-weighted KV blocks on
every cluster and either a non-makespan-optimal LPT order or >= 64 units
per cluster (7 contract rows per architecture): the persistent 2-CTA
grid draws its next unit from a per-cluster atomic ticket; the ticket of
unit k+1 is drawn at the head of unit k and consumed at its tail.
- **Publish-tail cut** (`SREAD_UNIFIED`) for the remaining SM100a plans:
stage 0 waits the other stage's score-read barrier before every P store,
removing a uniform compare + branch from the path between the last exp2
and the P stores. SM103a static plans keep the round-12 program.
- Generated programs: 11 programs, 3 new -- `dcc6cea1370b3bfaec30` (bf16
`attention`, replaces `d2a0d1f1d6f417bd8dc0`), `1350b7d87b8bb2dc9c46`
(bf16 `attention_dyn`), `08e428db13e7c3896d64` (bf16 `attention_sread`,
SM100a only); `579b1fc2756eec97f194` (combine) and the seven nvfp4
programs are unchanged; one new device helper
`cake_mbarrier_wait_cluster_0350e246f1666c26.cuh`
(`csrc/cake_minimax_h3_varlen_attention/...`); host text `cake_jit.py` /
`cake_backend.py`: per-plan program selection and `route_metadata`
disclosure (`cake_backend.py`: `BF16SegmentPlan.dyn_sched` /
`.sread_unified`, the `bf16_dyn_sched` predicate (`bf16_unit_weights`,
`bf16_cluster_work`), `bf16_attention_stage`, one extra `unit_table`
record (ticket counter) after the prefetch padding,
`runner.attention_stage` and the `attention_variant` / `dyn_sched` /
`sread_unified` keys of `route_metadata`; `cake_jit.py`:
`STAGES["bf16"]` = attention / attention_dyn / attention_sread / combine
with `stages_for(variant, arch)` (`BF16_SREAD_ARCHES = ("sm_100a",)`);
README: `unit_table` layout and the per-plan dispatch paragraph; tests:
dispatch predicate (rows + numbers), ticket-counter record, and a GPU
test that the dispatched program is bitwise the static one and that the
static program never writes the table).

## Measurements

CUPTI cold-L2 interleaved timing (paired A/B inside one process, arms in
contiguous blocks of 8 launches, identical-program control arm within
0.99-1.01; ratio = previous program / this program):

- Direct A/B against the round-12 program, all arms bitwise equal
(`torch.equal`): SM103a (40 rows timed, 1000 ms x 3): the 7 dynamically
scheduled plans 1.004-1.011, the other rows run the identical program
and read 0.996-1.036, none below 0.99. SM100a `SREAD_UNIFIED` (12 rows x
2 sessions + 19 rows x 1 session + 7 rows x 1 session): mean +0.3..+0.6
% on tail_5s_p1, dit_t2va, center_8s_p2, center_4s_p2, tail_5s_p2 x2,
dit_short_p1 (>= 1.000 in 5-6 of 6 rounds), within control noise
(|sigma| 0.25-0.79 %) on the other p1/p2 rows, the remaining 19 static
rows >= 1.000 on 19/19 (+0.1..+0.5 %); no row negative in both full
sessions.
- Standing against the fastest FlashInfer ragged route per row (fa2 /
cudnn / cutlass / cute-dsl / FA4, contract harness, two independent
sessions, a row counts only when >= 1.000 in both): SM103a 40/40 gated
rows standing in both sessions (geomean 1.064 / 1.064, min 1.009 /
1.006; round 12: 34/40); SM100a 33/37 standing (geomean 1.042 / 1.041;
round 12: 25/37), 4 rows within ~1.2 sigma below 1.000 against cute-dsl
(center_8s_p2 1.010 / 0.991, tail_5s_p1_m38531 1.001 / 0.996, dit_t2va
0.996 / 1.000, center_4s_p1 0.998 / 0.998), dit_2seg_p1 (second-session
control out of band) confirmed standing by a third session (1.017,
control 1.000)
- Generated-program export protocol (source/export parity, floor 0.97):
SM103a 120/120 rows passed, source/export ratio geomean 1.0008 (min
0.9867, max 1.0240), correctness and source/export bitwise identity on
every row; SM100a 120/120 rows passed, geomean 1.0000 (min 0.9853, max
1.0394), same correctness and bitwise checks

## Validation

- Cake: 56/56 contract rows correct on both architectures (atol = rtol =
1e-2) and bitwise equal to the previous program; FP32-oracle strict gate
(per-row max-abs <= round-4 + 1 BF16 ulp, RMS <= 1.01x) fails = 0 on
both architectures; compute-sanitizer synccheck + racecheck 0 errors (3
rows x 3 programs x both archs); e2e + bench-regression gates.
- FlashInfer:
`tests/experimental/test_cake_minimax_h3_varlen_attention.py` 653 passed
on SM103a (GB300) and 653 passed on SM100a (B200) after the export, run
from the exported checkout.

- Host text formatting: the generated `cake_backend.py` and the test
module were re-rendered through the export adapter after the ruff-format
pre-commit hook (ruff v0.12.8) reported over-long lines; the re-rendered
modules are AST-identical to the previous revision, and both
architectures' export protocols and FlashInfer test runs were repeated
on the re-rendered delivery (numbers above).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b77de25](https://github.com/flashinfer-ai/flashinfer/commit/b77de25d433ff5082247b8e306c3aa54857e3ed7)

- **作者**: Anerudhan Gopal
- **时间**: 2026-10-12T20:43:25Z
- **提交信息**: Fix KDA prefill metadata caches for inference tensors (#6372)

<!-- .github/pull_request_template.md -->

## 📌 Description

KDA prefill can raise `RuntimeError: Inference tensors do not track
version counter` when `cu_seqlens` is created under
`torch.inference_mode()`. Both the packed-offset metadata cache and
affine state-index carrier read `Tensor._version` without checking for
inference tensors. The affected helpers are identical in FlashInfer
0.7.1 and main at `c0e62fa7`.

This change skips version reads and eager cache reuse for inference
tensors. Normal tensors retain version-based cache invalidation. CUDA
graph capture still reuses warmed, fixed offset metadata and records
state-index copies for replay. Add regression tests for mutation, cold
capture rejection, and graph replay.

## 🔍 Related Issues

- Reported in [vLLM CI build
93957](https://buildkite.com/vllm/ci/builds/93957#01a123d4-00df-4a2d-8d81-dda11be7d084),
from vllm-project/vllm#60948.
- vllm-project/vllm#61250 already copies inference offsets into
contiguous, versioned int64 tensors. Its guard avoids this crash; this
fix needs no change to that PR.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

Changed-file hooks passed, including mypy and Ruff:

```sh
pre-commit run --files flashinfer/kda_prefill.py tests/kda/test_kda_prefill_inference_metadata.py
```

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Unmodified FlashInfer 0.7.1 reproduced all three reported failures on
GB300 (Torch 2.13.0+cu132, CUDA 13.2, CuTe DSL 4.7.1). The isolated
harness uses the unchanged CI adapter and three test bodies from vLLM
`da3cf3ad`, with real CUDA kernels and no backend override.

Post-fix GB300 validation passed with only this patch applied to the
same 0.7.1 release wheel:

| Test scope | Before | After |
| --- | --- | --- |
| Three unchanged vLLM CI test bodies: near-collinear keys, BF16
correctness, cross-stream breakable CUDA graph | 3 failed with the
version-counter error | 3 passed (33.82 s) |
| Added metadata mutation and CUDA graph tests | — | 8 passed (4.83 s) |

There were no post-fix test failures, collection errors or skips. The
metadata cases cover both regular and inference tensors, including
mutation, invalid offsets, cold capture rejection and state-index
updates on graph replay. The executed helper bodies match this PR's
commit `46a44472`. CuTe DSL deprecation warnings remain. These are
scoped tests; the full FlashInfer/vLLM suites and serving benchmarks
were not run.

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

Inference offsets have no mutation counter, so eager calls must reread
them instead of accepting an identity-only cache hit. This may add host
synchronization for these previously failing calls. Capture requires
offsets to retain their warmed values through replay; mutable state
indices still refresh through the captured copy. No public API or
backend selection changes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected metadata handling for inference-mode tensors. Offset changes
are now picked up on eager calls, while capture and replay use warmed
metadata.
* Improved handling of generated state indices when tensor version
information is unavailable.
* **Documentation**
* Clarified that packed offsets must retain their warmed values during
capture and replay, and that eager calls reread inference-mode offsets.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9cab083](https://github.com/flashinfer-ai/flashinfer/commit/9cab083bd9f19fcecf3c82cfc7b782f943b92d6e)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-12T19:49:02Z
- **提交信息**: Honor /bot run TEST_PATH in multi-GPU and multi-node CI jobs (#4643)

## Summary
- Multi-GPU and multi-node jobs still use their dedicated
`mpirun`/`torchrun` scripts and hardcoded file lists, but they now
intersect those lists with `TEST_PATH` (space-separated, same as `/bot
run tests/cli tests/trace_apply`).
- If a scoped run has no overlap, the job skips with exit 0 **before**
`install_and_verify`, so a targeted bot run does not execute unrelated
comm kernels.
- Unscoped `/bot run` (`TEST_PATH` empty) is unchanged.

Follow-up to #4641: unit jobs already honor `TEST_PATH`; these jobs
previously only printed the scoped banner and then ran the full
hardcoded suites.

## Test plan
- [x] `pytest tests/test_helpers/test_test_path_scope.py`
- [ ] `/bot run tests/cli tests/trace_apply` — multi-GPU/multi-node jobs
skip
- [ ] `/bot run tests/comm` — multi-GPU/multi-node still run overlapping
comm files
- [ ] `/bot run` with no path — same hardcoded lists as today

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **CI Improvements**
* Path-scoped multi-GPU and multi-node test jobs now skip successfully
when no relevant test files match the requested paths.
* Test environments are prepared only when matching tests need to run,
reducing unnecessary setup.
* Added support for matching individual files, directories, and multiple
requested paths.

* **Tests**
* Added coverage for path filtering, nested files, unrelated paths,
sibling-name matching, and setup ordering.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8b37094](https://github.com/flashinfer-ai/flashinfer/commit/8b37094e149c27e112d415fc92d1920c950f9ebd)

- **作者**: Fabio
- **时间**: 2026-10-12T19:26:32Z
- **提交信息**: feat(prims-ts): allow TMEM overlap for NVFP4 qkv overlap (#6286)

## 📌 Description

Extend TMEM accumulator overlap in the Prims-TS NVFP4 dense GEMMs to the
fused QKV + QKNorm + RoPE epilogue. Previously it was available for the
linear epilogue and, with #6255, for SwiGLU.

**Depends on #6255 (approved).** The first two commits are #6255
unchanged; only the last commit is new. I will rebase once #6255 is
merged.

TMEM overlap lets the MMA for the next output tile run while the current
tile's epilogue is still writing results, hiding epilogue time.

QKNorm reads the whole head before normalizing, so this epilogue needs a
small change to its store schedule: it keeps the first accumulator
subtile in registers, releases the accumulator after the norm reduction,
and then stores. This is supported for BF16 output with MMA-K 64.
Overlap remains opt-in (`tmem_overlap=True` in
`prepare_fp4_qkv_qknorm_rope`, also offered to the autotuner); defaults
are unchanged and results are bit-identical to the non-overlap kernel.

Performance (GB300, NVFP4 QKV+QKNorm+RoPE GEMM, N=9216, K=3072, BF16
output): 1.34x faster at M=8832 (195 → 146 us) and 1.44x at M=33408 (765
→ 533 us).

## 🔍 Related Issues

- Depends on https://github.com/flashinfer-ai/flashinfer/pull/6255

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [X] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [X] I have installed the hooks with `pre-commit install`.
- [X] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).

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

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Tensor-memory overlap now supports additional NVFP4 QKV QK-norm/RoPE
configurations with BF16 output and an MMA-K setting of 64. Existing
support for linear and SwiGLU operations remains available for supported
configurations.
* Preparation options for SwiGLU and QKV QK-norm/RoPE kernels continue
to let you enable tensor-memory overlap.
* **Bug Fixes**
* Added coverage confirming matching outputs with overlap enabled and
disabled for supported QKV configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [85ec446](https://github.com/flashinfer-ai/flashinfer/commit/85ec446e2ef04bcbae819779ee169ac01a33c365)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-12T18:55:31Z
- **提交信息**: fix(moe_ep): prepare weights for all configured compute backends (#6142)

<!-- .github/pull_request_template.md -->

## 📌 Description

`FusedMoeKernelConfig` forwards the configured compute backends to
`MoELayer`, but weight preparation returned after its first match. With
CuTe and TRT-LLM both enabled, the second runner could fail with
`Weights not prepared for backend ...` during selection.

Prepare a native weight view for every matching backend, sharing the
view when the same backend appears more than once. This lets split EP
use the existing backend and tactic selection while retaining explicit
single-backend configurations.

The bridge also omitted TRT-LLM W4A8 weights. Prepare those with the
configured MXFP4×MXFP8 quantization, and expose activation-scale bytes
in the `float8_e4m3fn` storage required by the unified API. The scale
view preserves the bytes; CuTe already reinterprets them as `uint8`.

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
and fixed any reported issues.

Changed-file hooks passed with `pre-commit run --files`; the full
repository hook run was not repeated.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Targeted validation:

- Host weight preparation, layer factory, bridge and config tests: 49
passed, 14 CUDA-dependent skips.
- CUDA weight preparation: 17 passed. Bridge tests: 12 passed. TRT-LLM
W4A8 bridge execution: passed.
- Existing TRT-LLM MXFP4 reference, autotuning and CUDA graph tests:
four passed.
- Four-rank NVFP4 correctness: six cases passed on each rank, covering
both layouts, both candidate orders and explicit TRT-LLM. Multi-backend
cases check backend selection and graph replay after changing
activations and routing in place.
- A manual W4A8 extension of the same distributed harness passed on all
four ranks for both layouts.

The regression tests check both FP4 quantization pairs, duplicate
candidates, singleton configurations and exact W4A8 scale bytes. CuTe
W4A8 eligibility is unchanged.

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

Enabling multiple backends retains their native weight views.
Eligibility checks, tactic tuning and the compute timing boundary are
unchanged; dispatch and combine are outside this selection.

### [03bd0aa](https://github.com/flashinfer-ai/flashinfer/commit/03bd0aa68bcb9778ef4c5a9bdbf5808b2f1fbb2d)

- **作者**: Brandon Zhang
- **时间**: 2026-10-12T18:05:13Z
- **提交信息**: feat(concat_mla_kv_quant_fp8): specialized kernel as a second backend, auto routing by head count (#5667)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #6163, which landed the public `concat_mla_kv_quant_fp8`
API (the fused MLA context K/V pack with saturating FP8 cast) backed by
generated Cake programs. That PR grew out of this one and replaced the
hand-written kernel this PR originally carried. This PR now adds that
hand-written kernel back as a **second backend** and routes between the
two by head count, so each shape gets the faster implementation:

```python
key, value = flashinfer.concat_mla_kv_quant_fp8(kv_nope, k_pe, key=None, value=None, *, nope_dim=128, backend="auto")
```

| backend | kernel | targets | layout requirements |
|---|---|---|---|
| `"specialized"` | hand-written CUDA kernel, one warp per token, fully
unrolled variant for 12 local heads, runtime head count otherwise
(`include/flashinfer/mla_kv_pack_fp8.cuh`) | every compute capability >=
10.0 | contiguous, 16-byte aligned |
| `"cake"` | generated Cake programs, one per head group (unchanged from
#6163) | exact SM 10.0 / 10.3 | 32-byte aligned; `k_pe` may be a
row-strided column slice |
| `"auto"` (default) | `"specialized"` for 12 local heads, `"cake"` for
every other head count; if the preferred backend cannot serve the call
the other is tried | | |

Everything no fused backend serves still takes the composable torch
path, and `FLASHINFER_SPECIALIZED_KERNEL_DISABLE=1` still forces it. An
explicit backend is never silently swapped: `backend="specialized"` with
a row-strided `k_pe` takes the torch path, not the Cake kernel.

**Why 12 heads.** 12 local heads is Kimi-K3's 96 heads over TP8, the
configuration the hand-written kernel was tuned on. #6163's own
measurements (interleaved CUPTI cold-L2 graph replays, 18 serving
shapes, B200 and B300) put the two kernels at the same copy floor there
with the hand-written one 0 to 3 % faster at every token count, and the
Cake programs 1.03x to 1.4x faster for every other head count (more
bytes in flight per warp). Our GB300 head-by-token sweep in the
deployment container showed the same shape of result: at 12 heads the
hand-written kernel beat vLLM's own fused kernel 1.11x to 1.29x on every
chunk size, while at 24 to 96 heads with small chunks it fell behind. So
`auto` takes the specialized kernel where it wins and Cake everywhere
else.

**Numerics are unchanged** on both backends: saturating e4m3 (round to
nearest even, finite overflow and +/-inf to +/-448, NaN to 0x7F),
byte-identical to the composable path.

**Internals.** Guards run GPU-free first (kill switch, dtypes, geometry,
contiguity, allowlist), then per-backend layout, then device, so the
fallback reasons #6163's tests pin are unchanged. The stats hook gains
`backend_dispatches` and `auto_specialized_heads`;
`specialized_dispatches` keeps counting every fused dispatch. The
specialized module joins the AOT inventory next to the Cake programs.
The allowlist JSON records the backends and the auto rule.

## 🔍 Related Issues

- #6163 (Cake programs behind this API; this PR stacks on it as merged)
- vllm-project/vllm#56881 (merged; vLLM's own fused kernel on the DCP
path, which a later vLLM PR will replace with this API)

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

`tests/utils/test_concat_mla_kv_quant_fp8.py`: the byte-exact matrix now
runs for `auto`, `specialized` and `cake` (each backend skips where its
targets are not built), and new tests pin the auto rule per head count
(`test_auto_routes_by_head_count`), the documented backend order, the
unknown-backend error and that an explicit backend is never silently
swapped. Cake-specific tests (strided `k_pe`, capture before JIT,
exact-target fallback) are marked `requires_cake` or pass
`backend="cake"`.

- RTX 5080 (SM 12.0: specialized live, Cake not built): 88 passed, 23
skipped.
- H100 (SM 9.0: both backends fall back): 44 passed, 63 skipped.
- The Cake-backed rows and `auto` on SM 10.0 / 10.3 need the B200 /
GB300 CI lanes.

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

The `backend` argument is hand-rolled rather than `@backend_requirement`
because this API's contract is "always runs, falls back to torch" and
the decorator's model is "raise when the backend cannot serve the call";
happy to switch if you prefer the decorator. The public signature only
gains the keyword-only `backend="auto"`; existing callers are
unaffected. AI assistance was used to prepare this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Signed-off-by: Brandon Zhang <31413216+brandonfzhang@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: nv-yunzheq <yunzheq@nvidia.com>

### [c0e62fa](https://github.com/flashinfer-ai/flashinfer/commit/c0e62fa7b18cbf051f729214984c235eb521a551)

- **作者**: Fabio
- **时间**: 2026-10-12T15:58:36Z
- **提交信息**: feat(prims-ts): allow TMEM overlap for NVFP4 SwiGLU epilogues (#6255)

## 📌 Description

Extend TMEM accumulator overlap in the Prims-TS NVFP4 dense GEMMs to the
fused SwiGLU epilogue. Previously it was only available for the linear
epilogue.

TMEM overlap double-buffers the accumulator so the MMA for the next
output tile runs while the current tile's epilogue is still writing
results, hiding epilogue time. This matters most for GEMMs with a short
K loop and a heavier epilogue such as SwiGLU.

The existing overlap kernel already handles the SwiGLU epilogue
correctly, for both BF16 and packed NVFP4 output, so this change only
makes the configuration available: it is accepted by the API
(`tmem_overlap=True` in `prepare_fp4_linear_swiglu`), allowed by the
tactic rules, and offered to the autotuner. Overlap remains opt-in;
defaults are unchanged and results are bit-identical to the non-overlap
kernel.

Performance (GB300, NVFP4 SwiGLU GEMM, N=18432, K=3072, packed NVFP4
output): 1.57x faster at M=8832 (331 → 211 us) and 1.60x at M=33408
(1179 → 738 us).

## 🔍 Related Issues
## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [X] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [X] I have installed the hooks with `pre-commit install`.
- [X] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).

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

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added tensor-memory overlap support for NVFP4 SwiGLU operations with
BF16 or NVFP4 output.
* The SwiGLU preparation option now lets you enable tensor-memory
overlap.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f63b2e7](https://github.com/flashinfer-ai/flashinfer/commit/f63b2e7cbfb9a008a3880ebf00f2bbf3721176fe)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-10-12T10:16:52Z
- **提交信息**: [feat] Add warp level split k mxfp8 gemm (#6167)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add a warp-level split-K runner for `mm_mxfp8(backend="cute-dsl")` on
SM100/SM103

## 📊 Performance

B300 SXM6, `mm_mxfp8(backend="cute-dsl")`, BF16 output, cold L2, CUPTI
kernel time under CUDA graph replay. Shapes are the #4908 table shapes
on which the warp runner is eligible. "Before" = tcgen05-only runner
set, "After" = with the warp split-K runner; each runs its own full
autotune. Times are medians over M.

| M | N | K | Before (µs) | After (µs) | Speedup |
| ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | 7168 | 768 | 5.71 | 4.00 | 1.43x |
| 2 | 7168 | 768 | 5.47 | 4.10 | 1.34x |
| 4 | 7168 | 768 | 5.92 | 4.13 | 1.43x |
| 6 | 7168 | 768 | 5.12 | 4.13 | 1.24x |
| 8 | 7168 | 768 | 5.15 | 4.19 | 1.23x |
| 12 | 7168 | 768 | 4.99 | 4.58 | 1.09x |
| 16 | 7168 | 768 | 5.02 | 4.62 | 1.09x |
| 1 | 1152 | 1536 | 4.51 | 3.84 | 1.18x |
| 2 | 1152 | 1536 | 4.53 | 3.94 | 1.15x |
| 4 | 1152 | 1536 | 4.42 | 3.09 | 1.43x |
| 6 | 1152 | 1536 | 4.58 | 4.14 | 1.10x |
| 8 | 1152 | 1536 | 4.58 | 4.06 | 1.13x |
| 12 | 1152 | 1536 | 4.56 | 3.22 | 1.42x |
| 14 | 1152 | 1536 | 4.58 | 3.22 | 1.42x |
| 16 | 1152 | 1536 | 4.58 | 3.23 | 1.42x |
| 1 | 2304 | 1536 | 6.40 | 3.55 | 1.80x |
| 2 | 2304 | 1536 | 4.96 | 3.74 | 1.32x |
| 4 | 2304 | 1536 | 6.50 | 3.55 | 1.83x |
| 6 | 2304 | 1536 | 5.63 | 3.55 | 1.59x |
| 8 | 2304 | 1536 | 5.63 | 3.58 | 1.57x |
| 12 | 2304 | 1536 | 5.70 | 3.90 | 1.46x |
| 14 | 2304 | 1536 | 5.73 | 3.94 | 1.46x |
| 16 | 2304 | 1536 | 5.73 | 3.94 | 1.46x |
| 1 | 4608 | 1536 | 6.24 | 4.50 | 1.39x |
| 2 | 4608 | 1536 | 5.86 | 4.46 | 1.31x |
| 4 | 4608 | 1536 | 5.92 | 4.48 | 1.32x |
| 6 | 4608 | 1536 | 5.70 | 4.51 | 1.26x |
| 8 | 4608 | 1536 | 5.70 | 4.54 | 1.25x |
| 12 | 4608 | 1536 | 5.84 | 5.12 | 1.14x |
| 14 | 4608 | 1536 | 5.89 | 5.09 | 1.16x |
| 16 | 4608 | 1536 | 5.86 | 5.15 | 1.14x |
| 1 | 2048 | 2048 | 5.31 | 4.08 | 1.30x |
| 2 | 2048 | 2048 | 6.72 | 3.81 | 1.76x |
| 4 | 2048 | 2048 | 6.37 | 3.97 | 1.60x |
| 6 | 2048 | 2048 | 6.46 | 4.16 | 1.55x |
| 8 | 2048 | 2048 | 6.42 | 4.16 | 1.54x |
| 12 | 2048 | 2048 | 5.46 | 4.38 | 1.24x |
| 14 | 2048 | 2048 | 5.47 | 4.38 | 1.25x |
| 16 | 2048 | 2048 | 5.47 | 4.45 | 1.23x |


## 🔍 Related Issues

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

Hooks were run on the changed files (mypy, ruff check, ruff format all
pass).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`tests/gemm/test_mm_mxfp8.py -k cute_dsl`: 16 passed on B300 (SM103).
`test_mm_mxfp8_cute_dsl_low_m` now runs both untuned and autotuned and
adds an M=8, K=4096 case, so the untuned path exercises the warp runner.
Not yet run on SM100 / B200.

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

- The kernel imports private helpers from
`dense_bf16_gemm_warp_splitk.py` (loader, `ldmatrix`, smem layout)
instead of duplicating them.
- `use_cold_l2_graph_replay` also changes how the existing tcgen05 MXFP8
runner is profiled; it was not A/B-tested separately for MXFP8.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a warp split-K execution path for supported MXFP8 matrix
multiplication workloads.
* **Improvements**
* Execution paths are selected based on input dimensions. The warp
split-K path is preferred for supported inputs when M ≤ 8 or K ≤ 2048.
* If a cached tuning choice is incompatible with the input, execution
falls back to a supported default.
* **Tests**
* Expanded MXFP8 coverage for small-M workloads, additional K
dimensions, autotuning, and repeated execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ae312f7](https://github.com/flashinfer-ai/flashinfer/commit/ae312f7cc1723b06fda5168105ade0f328ee47d8)

- **作者**: eigen
- **时间**: 2026-10-12T07:07:46Z
- **提交信息**: perf(cake_gdn): SM107a FP64-free q-scale, fp32 T=1 tilev32 band, chunked-parallel prefill route and native packed-KDA tile64 variant (#6323)

Follow-up to #6238 (merged). Same backend family as #5467 (@Vinnie6167,
FYI). Cake GDN decode on SM107a (Rubin, CC 10.7) only; SM100a / SM103a
kernel text is unchanged.

## What this PR does

Every Cake GDN decode kernel scales q by `(float)((double)x * SCALE)`.
On SM107a that FP64 multiply is now lowered to an exact FP64-free
helper, `cake_f32_mul_f64const_rn` (defined through
`cake_gdn_device_common.cuh` from a content-addressed
`csrc/cake_device_helpers/` file): bit for bit the same result as the
FP64 form for every input, with no FP64 instruction on the normal-input
path (the FP64 reference form stays out of line as `__noinline__` and is
reached only for subnormal / NaN / infinite inputs or a non-normal
result). The decode records therefore carry one kernel body per
architecture view: the shipped SM100a/SM103a body stays byte for byte as
`outputs[0]` and the SM107a view is a second output of the same record
(same symbol, launch and host shim); SM107a-only records (`_vpre`,
`_pro`, the SM107a band instances) get their re-derived body (the
previous body files are replaced). No SM100a/SM103a kernel text or
behaviour changes; outputs are bitwise identical on SM107a.

The fp32-state T=1 pretranspose row (H=16 / HV=32) additionally follows
a state-head band on SM107a: below 256 state heads the shipped `splitv8`
body (TILE_V 16, eight CTAs per state head), from 256 on its
`gdn_decode_pretranspose_splitv8_tilev32` twin (TILE_V 32, four CTAs per
state head; bitwise-identical output, only the row -> CTA mapping
changes), routed under `..._indexed_fp32_t1_splitv8_tilev32`. Two
SM107a-only records (SCALE 128^-0.5 and 1.0) are added; the host
launches B * HV times the CTAs per state head of the resolved record
(`cake_gdn_fp32_t1_ctas_per_state`) instead of a fixed eight, and each
shim checks that grid. SM100a/SM103a keep `splitv8` at every count.

The records are derived by the Cake exporter; the resolver overlay
(`flashinfer/jit/cake_gdn.py`) mirrors the band table
(`CAKE_GDN_FP32_T1_SPLITV8_ARCH_BANDS`), the resolver test covers the
rule and the per-view outputs, and `csrc/gdn/cake/README.md` documents
both.

## Behaviour notes reviewers should know

- `csrc/gdn/cake/manifest.json`: 15 decode records now list
per-architecture `outputs[]` (the SM100a/SM103a body first, the SM107a
view second). The JIT picks the view for the running architecture;
nothing changes for SM100a/SM103a callers.
- `cake_gdn_device_common.cuh` is extended append-only (two `#include`
lines for the helper and its `__noinline__` reference form). Existing
shipped lines are untouched.
- Exactness: the helper was checked exhaustively against the FP64 form
over all 2^32 float inputs for ten constants — the two shipped `SCALE`
values (128^-0.5 and 1.0) and eight stress constants (0.125, 0.0625,
2^-0.5, 2^-15, 1.2345678901234567, 1e-300, 1e300, -128^-0.5) — in a
plain build and under `--use_fast_math`: 0 mismatches (finite, subnormal
and NaN inputs). Constants representable in fp32 take the folded single
multiply, which is the same value.
- Compile line: the SM107a view of a hand-template record carries its
guarded specialization keys as baked `#define`s, so it compiles under
the shipped record's `-D` set.

## Validation (Rubin R200, SM107a, allocated compute)

| check | result |
|---|---|
| the nine Cake FlashInfer test files
(`tests/model_optimizations/test_dsv3_fused_routing.py`,
`tests/moe/test_cake_bgmv_moe.py`,
`tests/jit/test_cake_bgmv_moe_jit.py`, `tests/utils/test_concat_mla.py`,
`tests/gdn/test_cake_gdn_decode_gpu.py`,
`tests/gdn/test_cake_gdn_decode.py`,
`tests/gdn/test_cake_gdn_prefill_gpu.py`,
`tests/kda/test_packed_kda_decode.py`,
`tests/jit/test_cake_kda_packed_t1_jit.py`) at the pre-rebase commit
`9eb73e10487` (the same 24 files on top of the merged #6238 head) | 0
failing files |
| the same nine files at this head (`f12961f82`) | 0 failing files |
| compute-sanitizer synccheck + memcheck through the public path
(`backend="cake_gdn"`) at this head, 9 fp32-state rows that resolve to
six of the new SM107a bodies: pretranspose B=1 (`splitv8`), B=16 and
B=128 (`splitv8_tilev32`), nontranspose B=1/4 (small) and B=32/256
(large), fp32-MTP T=2 inline and T=4 `splitv8_pro`; the fp32-MTP T=4
`splitv2_tile64` view and the BF16-state SM107a views were not run under
the public-path sanitizer in this round | `ERROR SUMMARY: 0 errors`, 9/9
rows ok, both tools (also 0 errors on the pre-rebase commit) |
| Cake-side e2e `-m gpu -k gdn_decode` on the exporter commit | 89
passed |
| SM100a / SM103a / SM90a cubin identity of the exporter commit vs its
base, on a fixed 44-pair sample (4 shipped BF16-state GDN decode records
x SM100a/SM103a + 12 BGMV sources x SM90a/SM100a/SM103a); the 15
partitioned records keep their SM100a/SM103a body files unchanged
(`outputs[0]`) | 44 pairs IDENTICAL_CUBIN |
| Blackwell no-regression legs at this head vs its base `7cd20a82cae`:
B200 (SM100a) and GB300 (SM103a) — the same 44-pair cubin identity
sample, the nine Cake FlashInfer test files, and the Cake-side
five-family e2e slice | both all_pass: IDENTICAL_CUBIN; FlashInfer files
1676 passed / 0 failed on each; Cake e2e 315 passed / 7 skipped (B200),
285 passed / 37 skipped (GB300), 0 failed |

## Performance on R200 (interleaved cold-L2 CUPTI, paired arms, seeds 17
and 29; speedup = fastest non-Cake FlashInfer backend time / Cake time,
> 1 means Cake is faster)

Public path (`backend="cake_gdn"` vs the fastest other FlashInfer
backend), measured on the pre-rebase commit `9eb73e10487` (this PR's 24
files are byte-identical there; "before" = the merged #6238 head). The
fp32-state decode rows this PR changes, before and after:

| gdn_decode row | seed 17 | seed 29 | before this PR, seed 17 | before
this PR, seed 29 |
|---|---|---|---|---|
| `perf_pretranspose_b128` | 1.132 | 1.133 | 1.014 | 1.015 |
| `perf_nontranspose_b1` | 1.327 | 1.327 | 0.832 | 0.840 |
| `perf_nontranspose_b32` | 1.145 | 1.147 | 0.862 | 0.870 |
| `trace_nontranspose_b4_h4_hv8_zero_state_gates` | 1.340 | 1.337 |
0.838 | 0.852 |
| `correctness_nontranspose_b128_scale1_seed0` | 1.083 | 1.082 | 1.079 |
1.079 |
| `bench_pretranspose_b1` | 1.148 | 1.157 | 0.906 | 0.926 |
| `bench_pretranspose_b4` | 1.027 | 1.020 | 0.813 | 0.820 |
| `bench_pretranspose_b8` | 1.223 | 1.223 | 0.875 | 0.873 |
| `bench_pretranspose_b16` | 1.211 | 1.222 | 0.874 | 0.873 |
| `bench_pretranspose_b32` | 1.136 | 1.140 | 0.911 | 0.915 |
| `bench_pretranspose_b64` | 1.140 | 1.144 | 0.979 | 0.981 |
| `bench_pretranspose_b256` | 1.134 | 1.135 | 1.034 | 1.036 |
| `bench_pretranspose_b512` | 1.131 | 1.132 | 1.047 | 1.047 |
| `bench_nontranspose_b4` | 1.217 | 1.217 | 0.804 | 0.810 |
| `bench_nontranspose_b8` | 1.293 | 1.271 | 0.896 | 0.901 |
| `bench_nontranspose_b16` | 1.285 | 1.292 | 0.943 | 0.949 |
| `bench_nontranspose_b64` | 1.109 | 1.125 | 0.905 | 0.912 |
| `bench_nontranspose_b128` | 1.077 | 1.079 | 0.944 | 0.947 |
| `bench_nontranspose_b256` | 1.071 | 1.071 | 0.994 | 0.997 |
| `bench_nontranspose_b512` | 1.077 | 1.076 | 1.034 | 1.035 |
| `fp32mtp_b1_t2_verify_cache` | 1.008 | 1.000 | 0.875 | 0.879 |
| `fp32mtp_b4_t4_update_cache` | 1.209 | 1.204 | 0.861 | 0.855 |
| `fp32mtp_b16_t4_update_cache` | 1.323 | 1.294 | 1.181 | 1.275 |
| `fp32mtp_b64_t4_update_cache` | 1.051 | 1.048 | 1.021 | 1.004 |
| **geomean (24 / 24 measured rows)** | **1.1585** | **1.1578** | 0.9340
| 0.9402 |

Over all 42 measured GDN decode rows (BF16-state rows included; 9 TP4
BF16 rows have no non-Cake arm): geomean **1.2228** / **1.2204** /
0.9701 / 0.9779 (after, seeds 17 / 29, then before). No row is below 1.0
on either seed; the lowest is `fp32mtp_b1_t2_verify_cache` at 1.008 /
1.000 — on seed 29 that row ties the FlashInfer arm (4.16 vs 4.16 µs).
No public-path row errored (51 rows per seed); on the 42 two-arm rows
the Cake and FlashInfer outputs differ by at most 2.44e-4 (bf16 outputs)
and show identical max-abs error against the fp32 torch reference on 42
/ 42 rows. In the in-tree A/B all 21 output / state digests of the 15
fp32-state T=1 rows equal the FP64-form baseline.

## Round-2 commits on this PR (SM 10.7 only; SM100a / SM103a behaviour
unchanged)

Two follow-up commits on the same branch: `8e5316550` adds the Cake
chunked-parallel GDN **prefill** route on SM 10.7 with the fp32 SIMT
state fixup, and `bb43d155c` compiles the SM 10.7 tile-64 packed-KDA T=1
variant natively for `sm_107a`. Both are described below; the decode
content above is unchanged.

### Follow-up commit: Cake chunked-parallel GDN prefill on SM 10.7 with
the fp32 SIMT state fixup

Before this commit the `backend="cake_gdn"` prefill route on compute
capability 10.7 always ran the sequential Cake kernel, and on the 47
long-sequence rows below it was 0.18–0.92× FlashInfer's own
chunked-parallel (CP) prefill route, which is the device's default
`use_cp="auto"` route. This commit admits 10.7 to the Cake GDN CP
backend and routes `use_cp="auto"` into it inside an explicit, measured
band. SM100 / SM103 behaviour is unchanged (Cake CP there still only
with `use_cp=True`); `use_cp=False` still forces the sequential kernel
everywhere.

- `flashinfer/jit/cake_gdn_cp_backend.py`: the 27 non-UTCMMA CP programs
list `sm_107a`. The two UTCMMA (TF32) state-fixup programs stay SM100 /
SM103-only, so on 10.7 the state fixup is pinned to the fp32 SIMT row-4
kernel: no TF32 instruction on this architecture, and the accumulation
dtype of every program is unchanged.
- `flashinfer/gdn_prefill.py`: on 10.7 only, `use_cp="auto"` with
`backend="cake_gdn"` enters CP when `num_seqs * num_sab_heads <= 52`,
`max_seqlen >= 4096`, and the backend's own physical chunk plan pays off
(at least 6 chunks of at least 512 tokens per sequence, or chunks of at
least 4096 tokens); otherwise the sequential kernel runs as before.
- `flashinfer/gdn_kernels/blackwell/cake_gdn_cp_backend.py`: physical
chunk plan on the 212-SM part. The rounded-up chunk target leaves more
chunk CTAs than SMs for 32 and 48 state heads (224 / 240 CTAs, one CTA
per SM, chunk-major launch); the overflow CTAs are tail blocks that
start only after the first tail CTAs finish, so the critical path
becomes max(chunk, 2 · tail). When that second wave outlasts a chunk the
planner takes the one-wave floor target (6 × 11264 instead of 7 × 9728
for 32 heads at 65536 tokens; 4 × 16384 / 8192 / 4096 instead of 5 ×
13312 / 6656 / 3584 for 48 heads at 65536 / 32768 / 16384). Shorter rows
keep the rounded-up plan, which measures faster there. Other SM counts
are unchanged.
- `tests/gdn/test_cake_gdn_cp_backend.py`: the 212-SM physical plans (10
cases), the band predicate (14 cases); the explicit-route rejection test
uses compute capability 12.0 as its unsupported architecture.

**Numerical behaviour reviewers should know.** CP changes the
recombination structure (chunk-local states followed by the fp32 SIMT
fixup), not the precision of any accumulation. Against an fp64 per-token
reference on fixed inputs (the 47 rows below × 4 input sets, SM 10.7
device, two seeds), the maximum absolute and relative errors of `O`
(f16) and `final_state` (fp32) of the Cake CP route are identical to
those of FlashInfer's own CP route on the same device in all 752 (row,
tensor, statistic, input set) cells, with identical element-wise worse /
better counts (328 / 376): the public `cake_gdn` route on 10.7 is as
accurate as the device's default route. Relative to the sequential Cake
kernel (still the route outside the band, and on SM100 / SM103 under
`use_cp="auto"`), the `final_state` max-abs error is +9 % at the median
and at most +81 %; the `O` max-abs error is within 1.0× on 97 % of the
cells (max 1.44×). The probe commits did not change FlashInfer's own
route (its arm timing is 0.988–1.041× the base tree, median 1.005).

**Validation on the SM 10.7 device (allocated compute).** FlashInfer
tests at this head on the SM 10.7 device:
`tests/gdn/test_cake_gdn_prefill_gpu.py` 27 passed / 1 skipped (includes
the CUDA-graph capture and replay cases),
`tests/gdn/test_prefill_state_indices.py` 121 passed / 54 skipped,
`tests/gdn/test_cake_gdn_cp_backend.py` 372 passed / 18 skipped,
`tests/gdn/test_prefill_auto_backend.py` 2 passed,
`tests/kda/test_packed_kda_decode.py` 43 passed,
`tests/jit/test_cake_kda_packed_t1_jit.py` 93 passed (0 failing files).
compute-sanitizer synccheck and memcheck through the public path
(`backend="cake_gdn"`, `use_cp="auto"`) on 10 CP rows: `ERROR SUMMARY: 0
errors`, 10 / 10 rows ok, both tools. All 27 `sm_107a` CP programs
JIT-compile (22.5 s warm-up). Blackwell no-regression at this head on
B200 (SM100a) and GB300 (SM103a): the shipped SM100a / SM103a / SM90a
cubins stay byte-identical to the base (44 / 44 pairs on each device),
the nine Cake FlashInfer test files pass (1688 passed / 0 failed on
each; the 12 added cases are the new packed-KDA CPU tests), and the
Cake-side five-family e2e slice passes (B200 315 passed / 7 skipped,
GB300 285 passed / 37 skipped).

**Performance on the 212-SM SM 10.7 device** (interleaved cold-L2 CUPTI,
paired arms, seeds 17 and 29; speedup = fastest non-Cake FlashInfer
backend time / `backend="cake_gdn"` time, > 1 means Cake is faster). All
47 rows are above 1.0 on both seeds against every non-Cake arm
(FlashInfer `auto`, FlashInfer with `use_cp=False`): minimum 1.012 /
1.014, geomean 1.125 / 1.123; 40 rows route to CP and 7 to the
sequential kernel (1.06–1.21). Before this commit 37 of these rows were
below 1.0 (0.18–0.92, the sequential Cake kernel against FlashInfer's CP
route); the "before" columns of the table are the sequential kernel
measured in the same runs. The six 32- / 48-head rows at 16384–65536
tokens were 0.76–0.86 before the 212-SM plan rule and are 1.014–1.026
with it. `bench_hq2_hv8_1x8192` was re-measured twice more with
per-kernel CUPTI evidence (the second time on an otherwise idle node):
1.190 / 1.174 and 1.190 / 1.168 by GPU span; FlashInfer's four-launch CP
route carries about 13 µs of inter-kernel gaps on this row, and by
kernel-time sum alone the row is 1.023 / 1.014.

<details><summary>The 47 rows (public path, both seeds; the two "before"
columns are the sequential Cake kernel measured in the same
runs)</summary>

| row | `cake_gdn` route | seed 17 | seed 29 | before this commit
(sequential Cake kernel), seed 17 | seed 29 | Cake µs (17 / 29) |
fastest other backend µs (17 / 29) |
|---|---|---|---|---|---|---|---|
| `bench_hq2_hv8_1x65536` | cp | 1.012 | 1.014 | 0.183 | 0.182 | 225.2 /
227.7 | 228.0 / 230.8 (flashinfer) |
| `bench_hq2_hv8_1x32768` | cp | 1.015 | 1.018 | 0.242 | 0.241 | 149.2 /
150.6 | 151.4 / 153.3 (flashinfer) |
| `bench_hq4_hv16_1x65536` | cp | 1.026 | 1.023 | 0.309 | 0.304 | 377.5
/ 379.2 | 387.1 / 387.7 (flashinfer) |
| `perf_hq16_hv16_1x65536` | cp | 1.016 | 1.015 | 0.321 | 0.322 | 396.5
/ 397.2 | 402.6 / 403.3 (flashinfer) |
| `perf_hq2_hv8_1x16384` | cp | 1.042 | 1.040 | 0.337 | 0.334 | 102.1 /
103.3 | 106.5 / 107.4 (flashinfer) |
| `bench_hq4_hv16_1x32768` | cp | 1.036 | 1.029 | 0.363 | 0.362 | 223.9
/ 225.8 | 231.8 / 232.4 (flashinfer) |
| `perf_hq16_hv16_1x32768` | cp | 1.029 | 1.030 | 0.382 | 0.383 | 234.2
/ 234.7 | 241.0 / 241.9 (flashinfer) |
| `bench_hq4_hv16_1x16384` | cp | 1.075 | 1.065 | 0.487 | 0.489 | 146.0
/ 148.8 | 156.9 / 158.5 (flashinfer) |
| `bench_hq16_hv16_1x16384` | cp | 1.084 | 1.081 | 0.499 | 0.501 | 149.1
/ 150.0 | 161.5 / 162.3 (flashinfer) |
| `bench_hq2_hv8_1x8192` | cp | 1.753 | 1.779 | 0.833 | 0.842 | 76.7 /
77.6 | 134.4 / 138.1 (flashinfer) |
| `bench_hq8_hv32_1x65536` | cp | 1.026 | 1.025 | 0.559 | 0.560 | 712.9
/ 714.0 | 731.3 / 731.8 (flashinfer) |
| `bench_hq16_hv32_1x65536` | cp | 1.023 | 1.022 | 0.563 | 0.564 | 720.3
/ 721.5 | 736.6 / 737.1 (flashinfer) |
| `bench_hq32_hv32_1x65536` | cp | 1.014 | 1.014 | 0.570 | 0.571 | 741.6
/ 742.2 | 751.9 / 752.5 (flashinfer) |
| `bench_hq8_hv32_1x32768` | cp | 1.054 | 1.053 | 0.603 | 0.605 | 376.1
/ 377.3 | 396.5 / 397.3 (flashinfer) |
| `bench_hq16_hv32_1x32768` | cp | 1.053 | 1.051 | 0.612 | 0.613 | 380.8
/ 382.0 | 400.8 / 401.4 (flashinfer) |
| `bench_hq32_hv32_1x32768` | cp | 1.040 | 1.040 | 0.619 | 0.620 | 394.2
/ 394.8 | 410.1 / 410.7 (flashinfer) |
| `bench_hq4_hv16_1x8192` | cp | 1.159 | 1.138 | 0.700 | 0.704 | 99.8 /
102.5 | 115.6 / 116.6 (flashinfer) |
| `perf_hq16_hv16_1x8192` | cp | 1.148 | 1.127 | 0.710 | 0.715 | 101.8 /
104.4 | 116.8 / 117.7 (flashinfer) |
| `bench_hq8_hv32_1x16384` | cp | 1.083 | 1.078 | 0.718 | 0.720 | 220.9
/ 222.6 | 239.2 / 239.9 (flashinfer) |
| `bench_hq16_hv32_1x16384` | cp | 1.075 | 1.072 | 0.723 | 0.725 | 224.2
/ 225.6 | 241.1 / 241.8 (flashinfer) |
| `bench_hq32_hv32_1x16384` | cp | 1.065 | 1.062 | 0.733 | 0.735 | 230.9
/ 231.8 | 245.8 / 246.3 (flashinfer) |
| `bench_hq2_hv8_1024_7168` | cp | 1.400 | 1.402 | 0.815 | 0.810 | 82.4
/ 82.0 | 115.3 / 114.9 (flashinfer) |
| `bench_hq16_hv48_1x65536` | cp | 1.020 | 1.018 | 0.791 | 0.791 |
1028.6 / 1030.7 | 1049.5 / 1049.7 (flashinfer) |
| `bench_hq4_hv16_1024_7168` | cp | 1.056 | 1.056 | 0.810 | 0.809 |
111.8 / 111.8 | 118.0 / 118.1 (flashinfer) |
| `perf_hq16_hv16_1024_7168` | cp | 1.049 | 1.053 | 0.813 | 0.813 |
113.6 / 113.5 | 119.2 / 119.5 (flashinfer) |
| `bench_hq16_hv48_1x32768` | cp | 1.020 | 1.018 | 0.829 | 0.830 | 543.9
/ 545.2 | 554.7 / 554.9 (flashinfer) |
| `bench_hq2_hv8_2048_6144` | cp | 1.385 | 1.373 | 0.891 | 0.884 | 78.8
/ 79.0 | 109.2 / 108.4 (flashinfer) |
| `bench_hq2_hv8_6144_2048` | cp | 1.495 | 1.504 | 0.892 | 0.880 | 73.2
/ 73.1 | 109.5 / 109.9 (flashinfer) |
| `bench_hq2_hv8_1x4096` | cp | 1.354 | 1.345 | 0.928 | 0.910 | 57.3 /
57.6 | 77.6 / 77.5 (flashinfer) |
| `bench_hq8_hv32_1x8192` | cp | 1.029 | 1.022 | 0.882 | 0.887 | 145.7 /
147.6 | 149.9 / 150.8 (flashinfer) |
| `bench_hq4_hv16_6144_2048` | cp | 1.113 | 1.128 | 0.898 | 0.900 |
100.7 / 100.5 | 112.1 / 113.3 (flashinfer) |
| `bench_hq4_hv16_2048_6144` | cp | 1.065 | 1.069 | 0.892 | 0.898 |
105.6 / 105.9 | 112.4 / 113.2 (flashinfer) |
| `bench_hq16_hv32_1x8192` | cp | 1.029 | 1.019 | 0.883 | 0.887 | 147.0
/ 149.0 | 151.2 / 151.8 (flashinfer) |
| `perf_hq16_hv16_2048_6144` | cp | 1.068 | 1.068 | 0.900 | 0.903 |
107.3 / 107.6 | 114.6 / 114.9 (flashinfer) |
| `perf_hq16_hv16_6144_2048` | cp | 1.108 | 1.119 | 0.896 | 0.900 |
102.6 / 102.2 | 113.7 / 114.4 (flashinfer) |
| `bench_hq32_hv32_1x8192` | cp | 1.038 | 1.035 | 0.896 | 0.899 | 148.9
/ 149.9 | 154.5 / 155.1 (flashinfer) |
| `bench_hq16_hv48_1x16384` | cp | 1.023 | 1.022 | 0.908 | 0.909 | 300.4
/ 301.1 | 307.4 / 307.6 (flashinfer) |
| `perf_hq16_hv16_1x4096` | cp | 1.369 | 1.320 | 1.197 | 1.195 | 74.9 /
77.7 | 102.6 / 102.6 (flashinfer) |
| `perf_hq16_hv16_4096_4096` | noncp | 1.207 | 1.210 | 1.207 | 1.210 |
88.1 / 87.9 | 106.4 / 106.4 (flashinfer_noncp) |
| `bench_hq2_hv8_4096_4096` | cp | 1.319 | 1.308 | 1.195 | 1.185 | 76.4
/ 77.4 | 100.8 / 101.3 (flashinfer_noncp) |
| `bench_hq4_hv16_1x4096` | cp | 1.339 | 1.322 | 1.187 | 1.180 | 76.0 /
77.1 | 101.8 / 102.0 (flashinfer) |
| `bench_hq4_hv16_4096_4096` | noncp | 1.188 | 1.187 | 1.187 | 1.188 |
86.7 / 86.7 | 102.9 / 102.9 (flashinfer_noncp) |
| `bench_hq8_hv32_1x4096` | noncp | 1.199 | 1.204 | 1.197 | 1.206 | 89.5
/ 89.3 | 107.3 / 107.6 (flashinfer_noncp) |
| `bench_hq16_hv32_1x4096` | noncp | 1.203 | 1.205 | 1.201 | 1.206 |
89.4 / 89.2 | 107.5 / 107.5 (flashinfer_noncp) |
| `bench_hq16_hv48_1x8192` | noncp | 1.058 | 1.063 | 1.057 | 1.063 |
173.4 / 173.0 | 183.5 / 183.8 (flashinfer) |
| `bench_hq16_hv48_1x4096` | noncp | 1.168 | 1.176 | 1.166 | 1.178 |
91.3 / 90.9 | 106.6 / 106.9 (flashinfer_noncp) |
| `bench_hq32_hv32_1x4096` | noncp | 1.193 | 1.196 | 1.192 | 1.197 |
90.1 / 89.9 | 107.4 / 107.5 (flashinfer_noncp) |
| **geomean (47 rows)** | | **1.125** | **1.123** | 0.718 | 0.719 | | |

</details>

### Follow-up commit: packed KDA T=1 on SM 10.7 — native `sm_107a`
compile for the tile-64 early-publish variant

`cake_packed_kda_decode._target_for_variant` selects the JIT target per
qualified variant on compute capability 10.7:
`sm107a` for `cpasync_tile64_register_pipeline_early_publish` (the SM107
aligned band, batch 19–63), `sm100f` for
`register_tile16` (≤ 18), `cpasync_tile128_register_pipeline` (≥ 64),
the scalar-aux variants and the legacy route.
The kernel source is identical; the output and the state pool are
bitwise identical between the two targets
(42/42 row-runs over 18 batches × 2 seeds).

Measured on a 212-SM SM 10.7 device (CUPTI median, two seeds), family →
native µs: B20 5.02 → 4.67, B24 5.09 → 4.80,
B31 5.57 → 5.31, B32 5.70 → 5.44, B48 6.75 → 6.53, B56 7.30 → 7.07 (−3.1
… −7.0 %); outside the band the family cubin
stays faster (B16 4.10 vs 4.29, B64 8.06 vs 8.06, B128 11.87 vs 13.79),
which is why the selection is keyed by variant
rather than by device. Public route vs the CuTe packed kernel after this
change: minimum 1.012 over 21 batches (B1–B512), geomean 1.09; B24
1.020, B31 1.012–1.024, B32 1.012–1.018 at two seeds.

Tests: `tests/kda/test_packed_kda_decode.py` (+12 CPU cases: the
variant-keyed target table and the facade call
sequence for batches 16/19/32/63/64/128 on 10.7) and
`tests/jit/test_cake_kda_packed_t1_jit.py` pass on the SM 10.7 device.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4594
- **最后更新**: 2026-10-12T23:42:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34707
- **最后更新**: 2026-10-13T03:07:37Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Wang, Yi

## AI分析总结

## 分析总结

### 1. 主要更新类型
**功能新增**。本次提交明确针对XPU（Intel GPU）硬件增加了张量并行（TP）支持，属于对硬件后端的功能扩展。

### 2. 关键变更点与项目方向关系
- **变更核心**：在现有分布式并行策略基础上，为XPU设备补充实现了张量并行（TP）能力，使模型可利用多卡XPU进行分布式训练或推理。
- **与项目方向关联**：Diffusers作为扩散模型库，其核心目标之一是支持多样化硬件后端并优化生成效率。此次更新延续了项目“硬件友好性”与“性能可扩展性”的路线，填补了Intel XPU生态在并行策略上的空白。

### 3. 对项目的影响与潜在意义
- **短期影响**：提升在Intel XPU平台上的大规模模型运行效率，降低显存占用，并为XPU用户提供完整的分布式训练选项。
- **长期意义**：
  - 增强Diffusers对非NVIDIA硬件（如AMD GPU、Intel GPU）的覆盖，推动社区生态多元化。
  - 可能吸引更多Intel开发者及企业用户参与，加速硬件适配的良性循环。
  - 为后续其他并行策略（如流水线并行）在XPU上的实现奠定基础。

### 4. 值得关注的技术点
- **跨硬件抽象设计**：如何将TP机制抽象为与后端无关的接口，同时兼顾XPU的特定计算架构（如指令集、显存管理）。
- **分布式通信实现**：XPU上TP所需的通信原语（如all-reduce）可能采用不同通信库（如Intel的oneCCL），需验证其性能与兼容性。
- **与现有管线的集成**：需确保TP在XPU上的启用不影响其他后端（如CUDA、MPS）的现有功能。

### 5. 基于项目背景的发展影响
Diffusers旨在成为扩散模型领域的通用工具库，支持从研究到生产的全流程。README摘要虽主要体现Apache 2.0许可证，但结合项目实际，其核心价值在于**开放协作**与**硬件无关性**。本次提交：
- **强化开源生态**：体现了社区驱动对多样化硬件支持的趋势，符合开源项目“由社区共建通用基础设施”的发展逻辑。
- **促进技术民主化**：通过支持更多硬件，降低扩散模型在不同平台上的使用门槛，推动技术普及。
- **为规模化铺路**：张量并行是运行超大模型（如潜在空间扩散模型）的关键技术，XPU支持将帮助项目未来在更大规模生成任务中保持竞争力。

总体而言，此次更新虽看似针对特定硬件，实则反映了Diffusers在构建**全硬件覆盖、高性能生成式AI基础设施**上的持续努力。

## 详细提交记录

### [1e004eb](https://github.com/huggingface/diffusers/commit/1e004eb6ec9435349c4a6dd6d1c44c7e0fec6b40)

- **作者**: Wang, Yi
- **时间**: 2026-10-12T09:09:49Z
- **提交信息**: xpu supports TP as well (#15013)

xpu support TP as well

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
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


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13229
- **最后更新**: 2026-10-13T03:02:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37052
- **最后更新**: 2026-10-13T02:58:02Z

## 提交统计

- **昨日提交总数**: 38
- **提交者数量**: 31
- **主要提交者**: Alexandr, Anupa Sajikumar, Shuwen Wang

## AI分析总结

# SGLang 昨日提交分析（共38条）

## 1. 主要更新类型分布
- **平台适配与硬件支持**（约30%）：AMD/ROCm、NPU、Intel XPU、CUDA 多平台并行推进
- **性能优化与内核**（约25%）：FlashMLA/MegaAttention 内核、MXFP4/MXFP8 GEMM、HiCache 优化
- **Bug 修复与稳定性**（约25%）：CI 修复、调度器崩溃防护、并发原子性修复
- **功能新增**（约10%）：Anthropic Messages API、PD 并行策略
- **文档更新**（约5%）：Cookbook 与 playground 刷新

## 2. 关键变更点与项目方向的关系
- **DeepSeek V4.1 全面落地**：多条提交围绕 DSpark/DFlash PD 推理、DeepSeek V4 prefill 与 interleave CP（上下文并行）、NIXL 传输后端、flydsl MXFP8 dense GEMM 内核展开，表明项目正在全力支持最新 DeepSeek 模型架构，与 SGLang "高性能 LLM 推理" 的核心目标高度一致。
- **多硬件生态扩展**：AMD MI355X（MoRI 升级、AITER 适配）、Intel XPU（PyTorch 2.14 升级、DCP 解码上下文并行）、NPU（HiCache 稳定化、Qwen-VL 适配）齐头并进，强化了项目的跨平台推理服务能力。
- **投机解码（Speculative Decoding）深化**：EAGLE 首步 proposal distribution、DFlash 候选池统一决策、DSpark 共享 draft 参数等，持续打磨多级投机解码管线。

## 3. 对项目的影响与潜在意义
- **稳定性显著提升**：外部 linker 加载失败改为中止请求而非崩溃调度器、tokenizer 请求状态原子化初始化、PD 传输失败时的 ack 投毒机制，均降低了生产环境风险。
- **缓存体系成熟**：Unified Cache 与 HiCache 持续迭代（Mamba 支持、MTP KV 保留、消除迁移停顿、精确大小主机内存分配），为长上下文和混合模型推理铺路。
- **生态兼容性**：新增 Anthropic Messages API 端点（/v1/messages），降低了与 Claude 生态工具链的集成门槛。

## 4. 值得关注的技术点
- **CUDA Graph 增强**：CUDA graph capture 中修复 autograd 保留问题、捕获 KV 主机传输缓冲区、breakable CUDA graphs + CP 组合，推动图捕获在复杂场景的可用性。
- **AI 协作开发趋势**：多条提交出现 Claude Opus/Gable 等 AI 协作者署名，反映 LLM 辅助开发已深度嵌入该项目的工程流程。
- **CPU/GPU 亲和性**：diffusion worker 按 GPU 所在 NUMA 节点绑定 CPU，是细粒度性能调优的体现。
- **CI 成本优化**：按硬件需求重新划分测试套件（如 GB300 专用测试分离、NPU GT 图像缓存），提升 CI 效率。

## 5. 对项目整体发展的影响
基于 README，SGLang 定位为 LLM 与多模态模型的快速推理引擎。本批提交显示出三条清晰发展主线：(1) 以 DeepSeek V4.1 为代表的前沿模型首发级支持，巩固其"最快落地新模型"的竞争优势；(2) 以 AMD/Intel/NPU 为代表的多硬件后端成熟化，扩大部署覆盖面；(3) 以 HiCache、投机解码、CUDA Graph 为核心的推理管线深度优化，持续兑现性能承诺。同时，扩散模型（diffusion）相关的 NPU/XPU/CI 提交表明项目正将多模态生成纳入稳定的工程轨道，为从纯 LLM 推理平台向全栈多模态推理平台演进奠定基础。

## 详细提交记录

### [7224fce](https://github.com/sgl-project/sglang/commit/7224fce1b5e488c9916f20ec0556d696e595d512)

- **作者**: Michael
- **时间**: 2026-10-12T23:46:03Z
- **提交信息**: [AMD] Recalibrate test_quark_mxfp4 GSM8K thresholds to observed MI355X noise (#41980)

### [6a7abcf](https://github.com/sgl-project/sglang/commit/6a7abcfc9b603d494cdc58fa54bc793a915b547c)

- **作者**: Yizheng Jiao
- **时间**: 2026-10-12T22:32:17Z
- **提交信息**: [DeepSeek-V4.1] Admit the NIXL transfer backend for DSpark PD (#43734)

### [9380920](https://github.com/sgl-project/sglang/commit/93809202a3ffcf764c9bc0a9673ae83be69efc20)

- **作者**: Khoa Pham
- **时间**: 2026-10-12T21:50:04Z
- **提交信息**: [Kernel] Expose bundled FlashMLA MegaAttention kernels and APIs (#43918)

### [6781da8](https://github.com/sgl-project/sglang/commit/6781da8e5b9c8294cd02da2717317894b623d2bc)

- **作者**: Duyi-Wang
- **时间**: 2026-10-12T21:45:42Z
- **提交信息**: [AMD] [Docker] Update MoRI to v1.2.4 (#43834)

### [64cffed](https://github.com/sgl-project/sglang/commit/64cffed1390ed9da7cd89cd94fc16f5616f2ebb6)

- **作者**: Thomas Wang
- **时间**: 2026-10-12T21:43:19Z
- **提交信息**: [AMD] Fix test_compact_attention_hip.py CI (#43836)

### [d6853f5](https://github.com/sgl-project/sglang/commit/d6853f506658072d8b1db75d6b6d3faf55005916)

- **作者**: Thomas Wang
- **时间**: 2026-10-12T21:42:02Z
- **提交信息**: [AMD] Add flydsl mxfp8 dense gemm kernel for dpsk v4.1 prefill (#43803)

### [6c2a682](https://github.com/sgl-project/sglang/commit/6c2a682b59bdd1bfbdb809b664579586a96b3b95)

- **作者**: Michael
- **时间**: 2026-10-12T21:39:08Z
- **提交信息**: [AMD] Keep the FP4 varctx schedule test off AITER's 2048-row compile (#41793)

### [6966c5d](https://github.com/sgl-project/sglang/commit/6966c5d027163f1d2005e5fec8e0ed40cf95213e)

- **作者**: Zhang, Jiejing
- **时间**: 2026-10-12T21:05:51Z
- **提交信息**: [ROCm] Eliminate HiCache migration stalls and use exact-size host allocations (#42553)

Signed-off-by: JohnQinAMD <yanyuan.qin@amd.com>
Co-authored-by: JohnQinAMD <yanyuan.qin@amd.com>

### [b60444c](https://github.com/sgl-project/sglang/commit/b60444c62169c7992b98f102cbc4e86d9d117294)

- **作者**: ix-48
- **时间**: 2026-10-12T19:31:18Z
- **提交信息**: Fix autograd retention in CUDA graph capture tail hooks (#43854)

### [0efbb3d](https://github.com/sgl-project/sglang/commit/0efbb3d2b947b94f8ec6ce46120db01a4be367ae)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-12T18:35:57Z
- **提交信息**: [DFlash] Decide the Domino candidate pool in one place and apply simulated acceptance inside the accept (#43791)

### [392039d](https://github.com/sgl-project/sglang/commit/392039d752505af21ec765a7c4df0e28a2adfcbe)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-12T18:35:41Z
- **提交信息**: [DSpark] Share draft params, logits dtype, confidence and the accept tail between graph and eager (#43790)

### [f92199b](https://github.com/sgl-project/sglang/commit/f92199b569d2083c530f0e0a1a7b28879fa6404f)

- **作者**: Shuwen Wang
- **时间**: 2026-10-12T16:03:21Z
- **提交信息**: [Unified Cache] Abort requests whose external linker load fails instead of crashing the scheduler (#40896)

### [d88d5c3](https://github.com/sgl-project/sglang/commit/d88d5c325ad1cf28f2b804edcd8886e891a8f9b8)

- **作者**: Sam Shleifer
- **时间**: 2026-10-12T15:27:21Z
- **提交信息**: Prebuild fixup_zero_kv JIT module at TRTLLM-MLA backend init (#37525)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [23a1f53](https://github.com/sgl-project/sglang/commit/23a1f53fc3a0e7f5fc94c4a4abd4eb9bcf9c6042)

- **作者**: Yuan Luo
- **时间**: 2026-10-12T14:47:45Z
- **提交信息**: [QSA] Bound the decode indexer's work by the context length (#43463)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [1a55392](https://github.com/sgl-project/sglang/commit/1a553927b0b200f787a9eb350c563a3d84b1c785)

- **作者**: Alexandr
- **时间**: 2026-10-12T14:18:01Z
- **提交信息**: [CI][Diffusion] Add caching for npu GT images in CI (#37426)

Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>

### [279f1fa](https://github.com/sgl-project/sglang/commit/279f1fad907dd53044a7b68fcc45bd6a24467c9e)

- **作者**: Mick
- **时间**: 2026-10-12T13:09:41Z
- **提交信息**: [diffusion] chore: bind worker CPUs to the GPU's NUMA node when memory policy is not permitted (#43756)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d1357bf](https://github.com/sgl-project/sglang/commit/d1357bf87bfa836000c0620aef7504646ac049d8)

- **作者**: Артем Савкин
- **时间**: 2026-10-12T11:53:51Z
- **提交信息**: [NPU] Diffusion CI fixes (#43210)

### [c6e822c](https://github.com/sgl-project/sglang/commit/c6e822c29b9bb3d392e65a7bcb271a5d2d63613d)

- **作者**: ming_wang
- **时间**: 2026-10-12T11:24:05Z
- **提交信息**: [Fix] Adapt NPU Qwen-VL processor patch to transformers 5.19 resize() signature change (#43309)

### [7953751](https://github.com/sgl-project/sglang/commit/7953751bfa83239e1dad6dd3a45864db8ce28021)

- **作者**: Sasha Sidorov
- **时间**: 2026-10-12T10:49:52Z
- **提交信息**: [PD][Spec] Give a PD decode's first EAGLE draft step a proposal distribution (#41783)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [8afe107](https://github.com/sgl-project/sglang/commit/8afe107c24b9756c927498c4eb449499e9aabb2c)

- **作者**: Pavan Sivaram Girijala
- **时间**: 2026-10-12T10:24:48Z
- **提交信息**: [XPU] Upgrade XPU backend to PyTorch 2.14 (#42003)

Co-authored-by: Ashwini Rathi <arathi@habana.ai>
Co-authored-by: Y <ashwini.rathi@intel.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [2862173](https://github.com/sgl-project/sglang/commit/28621739fc6e8084b59f0b02178413f993e35afb)

- **作者**: C
- **时间**: 2026-10-12T10:10:57Z
- **提交信息**: [Fix] Make tokenizer request-state initialization atomic (#41911)

Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>

### [1809335](https://github.com/sgl-project/sglang/commit/180933518ea57f1f3c933db1c150211a57214900)

- **作者**: ybyang
- **时间**: 2026-10-12T09:56:08Z
- **提交信息**: [sgl-router] Serve the Anthropic Messages API on /v1/messages (#42316)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [f006fb4](https://github.com/sgl-project/sglang/commit/f006fb49ecd93322802ddebff80821f8e6296893)

- **作者**: Jinyan Yi
- **时间**: 2026-10-12T09:10:26Z
- **提交信息**: [NPU] Stabilize HiCache and registered CI tests (#43308)

### [b0c84d4](https://github.com/sgl-project/sglang/commit/b0c84d45189af373e60288b9c45d35a0e8657874)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-12T09:08:11Z
- **提交信息**: [Docs] Cookbook: refresh SemiAnalysis AgentX launches (GLM-5.2 B300, DeepSeek-V4.1 GB300) (#43799)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [450837e](https://github.com/sgl-project/sglang/commit/450837e770ce5f396e809942f6a8a3391c3f6854)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-12T08:38:12Z
- **提交信息**: [Docs] Update GLM-5.3-Flash playground: B300 default, CP8, EP and PD (#43802)

### [62ff466](https://github.com/sgl-project/sglang/commit/62ff466ac0c2cdd5521acf7d4c673fa7630eb083)

- **作者**: BingjiaWang
- **时间**: 2026-10-12T08:05:21Z
- **提交信息**: [DSV4.1][PD][1/N] Support prefill node use cp parallel strategy (#40323)

### [54409c2](https://github.com/sgl-project/sglang/commit/54409c2fa0812b5801197db658f695335f484c48)

- **作者**: BingjiaWang
- **时间**: 2026-10-12T08:03:10Z
- **提交信息**: [BCG][DSV4-Flash][CP] Support DeepSeek V4 prefill with interleave CP and breakable CUDA graphs (#38603)

### [8d491fb](https://github.com/sgl-project/sglang/commit/8d491fbc3e03859f232d37a117846873b29e590d)

- **作者**: Anupa Sajikumar
- **时间**: 2026-10-12T07:50:33Z
- **提交信息**: [XPU] Support decode context parallelism (DCP) on Intel XPU (#34355)

Co-authored-by: Siju Samuel <siju.samuel@intel.com>

### [a70a83b](https://github.com/sgl-project/sglang/commit/a70a83bcd237b7de6136574f47515a58bf9efd83)

- **作者**: Ke Bao
- **时间**: 2026-10-12T07:40:59Z
- **提交信息**: Keep NIXL Mamba checkpoint keys separate by TP rank (#43594)

### [b6ba148](https://github.com/sgl-project/sglang/commit/b6ba1483848dda193c18f9cf9d0cb52f0de60d34)

- **作者**: Ke Bao
- **时间**: 2026-10-12T07:40:06Z
- **提交信息**: Capture KV host transfer buffers (#43711)

### [0688782](https://github.com/sgl-project/sglang/commit/06887827c7df060f472a99dacb9267331187f0bc)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-12T07:38:10Z
- **提交信息**: [CI] Move tests that do not need GB300 off the per-PR GB300 suite (#43784)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [5ca0695](https://github.com/sgl-project/sglang/commit/5ca0695aa69f891bf98a57e7dd83cf75f1bc24c6)

- **作者**: paulzhang-tm
- **时间**: 2026-10-12T07:37:59Z
- **提交信息**: [HiCache] Preserve all MTP KV and recurrent state (#40223)

Co-authored-by: alphabetc1 <2508695655@qq.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [f5f5003](https://github.com/sgl-project/sglang/commit/f5f5003323ea42fae3193dd0e39dabf3b430e457)

- **作者**: Shuwen Wang
- **时间**: 2026-10-12T07:35:16Z
- **提交信息**: [HiCache] Support Mamba in buffer-only host memory mode (#36345)

### [4195980](https://github.com/sgl-project/sglang/commit/4195980f5a3d1efd9d1ab5d8a6c368b94122c950)

- **作者**: Shangming Cai
- **时间**: 2026-10-12T07:33:09Z
- **提交信息**: [PD] Poison the deferred abort ack when a Mooncake send fails (#43719)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [da4bf1e](https://github.com/sgl-project/sglang/commit/da4bf1ef8ebc8af119b3f7740b0d7a3ee281055a)

- **作者**: Chunan Zeng
- **时间**: 2026-10-12T07:27:22Z
- **提交信息**: [Perf] Route BF16 mixed-batch decode tails through decode attention (#43238)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [a0e6eff](https://github.com/sgl-project/sglang/commit/a0e6effe506ac266b41875d8281b4cacd0e71fb3)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-12T07:26:32Z
- **提交信息**: [Fix] Link cuda_ipc JIT against CUDA driver stubs dir (#43764)

### [62c853b](https://github.com/sgl-project/sglang/commit/62c853b6547c00c2528e4a24351c37f2f9689923)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-12T07:24:57Z
- **提交信息**: docs: clarify prefill CP terminology and simplify wording (#43787)

### [208df29](https://github.com/sgl-project/sglang/commit/208df292e541246c4b88a11131474c804119047b)

- **作者**: Yihao Wang
- **时间**: 2026-10-12T07:16:58Z
- **提交信息**: [diffusion][xpu] FLUX.2: enable the bit-exact Triton SwiGLU on XPU (#41940)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1290
- **最后更新**: 2026-10-10T08:39:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93676
- **最后更新**: 2026-10-13T03:05:48Z

## 提交统计

- **昨日提交总数**: 66
- **提交者数量**: 55
- **主要提交者**: SeongJun Lee, Giancarlo Delfin, Ilya Boytsov

## AI分析总结

# vLLM 昨日提交总结（共 66 个提交）

## 主要更新
- **Bug 修复（约 40%）**：覆盖 Rust 前端、KV Connector、LoRA、多模态、MoE、投机解码、structured output 等子系统。
- **性能优化（约 30%）**：集中于 ROCm/Meta 后端、MoE 内核、采样内核与注意力机制。
- **功能新增（约 20%）**：MoE 专家剪枝、准入拒绝指标、新模型适配（LiquidAI d1-3B、Cloudflare clef-omni）、Rust 前端指标增强。
- **重构与治理（约 10%）**：csrc 头文件整合、CI 分片限速、CODEOWNERS 调整、文档修复。

## 关键变更与项目方向
- **Rust 前端走向生产级**：时序指标、采样参数输出、请求 ID 处理、logprob、grammar/parser 重构、DP 路由修复、权重版本 span，表明项目正将全功能 OpenAI 兼容 API 层迁移至 Rust，呼应"快速、廉价服务"定位。
- **MoE 与大规模模型**：MoNe 专家剪枝、EPLB 草稿模型支持、CUTLASS FP4 expert_map 修复、ROCm 侧共享专家融合进 AITER MegaMoE，直接服务 DeepSeek V4 系列等大 MoE 的低成本部署。
- **稀疏注意力 HiSparse**：workspace 可配置化、host pool 容量日志、TP 组挂死修复，正从实验走向可用。
- **硬件多元化**：ROCm 获得批量不变性（batch invariance）、MLA 元数据构建 host 开销降低 21 倍、Gemma AR+RMS 回退修复、AITER nightly 脚本；Intel XPU 修复算子参数透传与 sleep mode 内存释放，体现"for everyone"的普惠目标。
- **可观测性**：按 watermark 状态统计完成请求数、准入拒绝指标、Rust 前端时序与版本追踪，利于 SRE 监控、灰度发布与容量规划。

## 项目影响
多模态 chunk 边界检查、投机解码草稿配置、structured output 任务排空等修复减少生产边界故障；本地 HF snapshot 加载 tokenizer/processor 降低启动延迟与网络依赖；删除 cascade attention、整合头文件、清理死代码降低维护成本。来自 Red Hat、AMD、Meta、Intel、NVIDIA 的贡献与 CODEOWNERS 更新，显示健康的多厂商共建生态与迭代期的质量管控。多个提交的 Co-authored-by 含 AI 助手，反映 AI 已深度参与开发流程。

## 值得关注的技术点
- **MoNe 专家剪枝**：首个 MoE 稀疏化支持，可显著压缩专家激活开销。
- **ROCm MLA host dispatch 降低 21 倍**：AMD 平台上 MLA 模型的 CPU 开销数量级改善。
- **AITER MegaMoE 融合策略**：跨专家类型的 kernel 融合，或成 MoE 加速通用范式。
- **批量不变性**：量化模型精度一致性的关键保障。
- **topk/topp masked logits 内核优化**：采样热路径优化，高并发短序列收益明显。
- **能力驱动的条件优化**：投机解码按后端是否支持元数据构建动态跳过冗余构建，设计优雅。
- **Triton 内核迁移 off `tl.make_block_ptr`**：为 triton-main 兼容性做前瞻性适配。

## 整体判断
vLLM 处于多线并进的成熟期：深度打磨 Rust 前端作为下一代默认服务层，同时在稀疏注意力、MoE 优化、多硬件支持三个方向持续加码，均指向大 MoE 模型低成本高吞吐部署这一核心命题，与"为所有人提供简单、快速、廉价的 LLM 服务"的愿景高度一致。

## 详细提交记录

### [189bbfb](https://github.com/vllm-project/vllm/commit/189bbfb9f432e283e21dcdf2a78357ae5db05ace)

- **作者**: Ilya Boytsov
- **时间**: 2026-10-12T23:18:43Z
- **提交信息**: Add MoNe experts pruning support (#50415)

Signed-off-by: Ilya Boytsov <ieboytsov@nebius.com>
Signed-off-by: Misha Goin <mgoin64@gmail.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Ilya Boytsov <ieboytsov@nebius.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1484266](https://github.com/vllm-project/vllm/commit/148426693823ec8fa27c353a1f8b5b9f7d402d8c)

- **作者**: Tomas Ruiz
- **时间**: 2026-10-12T23:01:11Z
- **提交信息**: [Perf] Improve `_topk_topp_kernel()` for masked logits (#61213)

Signed-off-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [1bc6e07](https://github.com/vllm-project/vllm/commit/1bc6e072b0ae402db5b7f054fc4d862eeb3067ea)

- **作者**: xinnywinne
- **时间**: 2026-10-12T22:39:10Z
- **提交信息**: [Rust Frontend] Add per-request timing metrics to chat and completions (#59314)

Signed-off-by: wxin <wxin@nvidia.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [802feb6](https://github.com/vllm-project/vllm/commit/802feb6770a0522ce8d2999262d95f4618e04adf)

- **作者**: Akshay Viswanathan
- **时间**: 2026-10-12T22:29:31Z
- **提交信息**: [Bugfix][KVConnector] Fix MoRI-IO WRITE-mode requests stranded in WAITING_FOR_REMOTE_KVS (#57705)

Signed-off-by: Akshay Viswanathan <4953343+akshayv@users.noreply.github.com>
Co-authored-by: Akshay Viswanathan <4953343+akshayv@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>

### [44f0ddf](https://github.com/vllm-project/vllm/commit/44f0ddfd7b61e200aac323231dfc127d4cd53cfb)

- **作者**: Maroon Ayoub
- **时间**: 2026-10-12T21:28:35Z
- **提交信息**: [Bugfix][Parser] Stop re-parsing the whole GLM tool argument per chunk (#61253)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [69d54eb](https://github.com/vllm-project/vllm/commit/69d54eb078db7ff9dd63f94d55a139b182c1776d)

- **作者**: Almog Tavor
- **时间**: 2026-10-12T21:26:43Z
- **提交信息**: [Docs] Fix broken llm-d.ai links on the llm-d integration page (#61022)

Signed-off-by: Almog Tavor <almogtavor@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [fe341a5](https://github.com/vllm-project/vllm/commit/fe341a53dda00472c281a2d1f4bd34a74e7eae6e)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-12T20:49:49Z
- **提交信息**: [HiSparse] Report host pool in KV cache capacity logs (#60285)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [deedc7b](https://github.com/vllm-project/vllm/commit/deedc7be008fe93473ca621936cde4f3c6ca1610)

- **作者**: SeongJun Lee
- **时间**: 2026-10-12T20:24:12Z
- **提交信息**: [Perf][Humming] Skip the redundant MoE input copy before the w13 GEMM (#59340)

Signed-off-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [654b725](https://github.com/vllm-project/vllm/commit/654b725ea9cb11085bce072a22a5e85709aafee6)

- **作者**: Andrey Talman
- **时间**: 2026-10-12T20:23:53Z
- **提交信息**: [CI] Pace the CRCR nightly report under the relay rate limit (#61269)

Signed-off-by: Andrey Talman <atalman@fb.com>

### [abad32a](https://github.com/vllm-project/vllm/commit/abad32a718d2f9e3af7b18818eb474322eaadfc4)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-12T19:53:08Z
- **提交信息**: [ROCm][Perf] Fix Gemma AR+RMS prefill fallback (#58547)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Signed-off-by: Mikko Tukiainen <mikko.tukiainen@amd.com>

### [fabaecb](https://github.com/vllm-project/vllm/commit/fabaecbfa5d48389cc8921d782b3f7d3aa0d928f)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-12T19:32:25Z
- **提交信息**: [Misc] Expand @ZJY0516 CODEOWNERS to Mamba and KV cache (#61181)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [7039c7f](https://github.com/vllm-project/vllm/commit/7039c7f17b5190862ab94ec476419c9127f2f400)

- **作者**: Martin Hickey
- **时间**: 2026-10-12T19:31:03Z
- **提交信息**: [Bugfix][Rust Frontend] Omit unset sampling params in render output (#61220)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [1bdd3fa](https://github.com/vllm-project/vllm/commit/1bdd3fa2d509ce8c40d92238050433822ce76d22)

- **作者**: ztysth
- **时间**: 2026-10-12T19:25:35Z
- **提交信息**: [Bugfix][Core] Check multimodal chunk boundaries before encoder cache reuse (#59721)

Signed-off-by: ztysth <rnk.liulw@gmail.com>
Signed-off-by: ztysth <166926442+ztysth@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [0858294](https://github.com/vllm-project/vllm/commit/08582942d8af7fc58339f3a5fedaffbbc8ea9f02)

- **作者**: Martin Hickey
- **时间**: 2026-10-12T19:17:12Z
- **提交信息**: [Bugfix][Frontend] Honor request_id and X-Request-Id in chat and completions render (#61236)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [d0948f7](https://github.com/vllm-project/vllm/commit/d0948f754dd1fa9a77721c5e9d3722036e74e6a7)

- **作者**: Wentao Ye
- **时间**: 2026-10-12T19:13:23Z
- **提交信息**: [Bug] Honor spec decode draft model config (#61240)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d6aca83](https://github.com/vllm-project/vllm/commit/d6aca837c3c6b773a557448d526db219a5a5718b)

- **作者**: Maroon Ayoub
- **时间**: 2026-10-12T18:56:51Z
- **提交信息**: [Attention] Make the sparse MLA prefill workspace size configurable (#61023)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [56e3b08](https://github.com/vllm-project/vllm/commit/56e3b081aea454d407ff658b3b12a5692f54fa47)

- **作者**: SeongJun Lee
- **时间**: 2026-10-12T18:33:31Z
- **提交信息**: [Bugfix][weight loader] Stop warning when a parameter only widens the weight (#60020)

Signed-off-by: lesj0610 <lesj0610@gmail.com>
Co-authored-by: Ning Xie <andy.xning@gmail.com>

### [8055293](https://github.com/vllm-project/vllm/commit/8055293353e4bc2aee2775bc0b077dd77b946b8c)

- **作者**: fululi12
- **时间**: 2026-10-12T18:11:20Z
- **提交信息**: [ROCm][MLA] Cut ~21x host dispatch from the MLA metadata build (#58381)

Signed-off-by: lifulu <fululi12@amd.com>
Signed-off-by: lifulu <lifulu@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: lifulu <lifulu@users.noreply.github.com>

### [c9e62f1](https://github.com/vllm-project/vllm/commit/c9e62f13c2b52619d8bc99f0c76cf04e77bff3c0)

- **作者**: josh-schell-amd
- **时间**: 2026-10-12T18:04:37Z
- **提交信息**: [CI][ROCm] Add AITER nightly overlay scripts (#60883)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [e1a5086](https://github.com/vllm-project/vllm/commit/e1a5086256a00c47a968aac6a583c25d040100a7)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-12T17:41:07Z
- **提交信息**: [Attention] Remove cascade attention (#61126)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5b0b8f2](https://github.com/vllm-project/vllm/commit/5b0b8f251ea6b878a22d85baba56e127c66297c8)

- **作者**: Maroon Ayoub
- **时间**: 2026-10-12T17:38:12Z
- **提交信息**: [Bugfix][HiSparse] Fix TP group hang on steps without scheduled tokens (#60941)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a7b7bc1](https://github.com/vllm-project/vllm/commit/a7b7bc1fbe1f5c4e47c53b0f02a3ecfbcd8054b9)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-12T17:21:22Z
- **提交信息**: [Metrics] Count finished requests by watermark status (#58715)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [45bb710](https://github.com/vllm-project/vllm/commit/45bb710ecaa2f0e100d1cab27308186e9f4aa7dd)

- **作者**: Misha Goin
- **时间**: 2026-10-12T17:11:26Z
- **提交信息**: [CI] Add nightly Python 3.14 smoke test (#60456)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [12e6a58](https://github.com/vllm-project/vllm/commit/12e6a585ae020cdcef9ba61aae45eec5ba29591d)

- **作者**: Laith Sakka
- **时间**: 2026-10-12T17:09:57Z
- **提交信息**: [Fix][Compile] Declare group_shape in the static FP8 quant fusion … (#61108)

Signed-off-by: Laith Sakka <lsakka@meta.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c599b59](https://github.com/vllm-project/vllm/commit/c599b5971faf7ed8bff4bd1b14713293c20082d6)

- **作者**: Chester
- **时间**: 2026-10-12T17:05:55Z
- **提交信息**: [Bugfix][Frontend] Return all logprobs when completions requests logprobs=-1 (#55717)

Signed-off-by: Chester <42577861+superdiaodiao@users.noreply.github.com>

### [6e6e860](https://github.com/vllm-project/vllm/commit/6e6e86078afe73af5180a9888e88751d51ef1b31)

- **作者**: haotiaa
- **时间**: 2026-10-12T17:05:34Z
- **提交信息**: [Bugfix][Platform] Don't resolve current_platform during import vllm (#60766)

Signed-off-by: Haotian An <haotiaa@amazon.com>

### [fa39582](https://github.com/vllm-project/vllm/commit/fa39582756dcbf25b65cc36d8daa465b19134372)

- **作者**: Misha Goin
- **时间**: 2026-10-12T17:00:47Z
- **提交信息**: [Frontend] Serve LiquidAI/d1-3B on /v1/systemone (#60676)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d79b52b](https://github.com/vllm-project/vllm/commit/d79b52b18219ecbaba780f72ae0a4aa0546ac00f)

- **作者**: Misha Goin
- **时间**: 2026-10-12T16:46:22Z
- **提交信息**: [Misc] Consolidate csrc shared headers and prune dead code (#60721)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e0317b2](https://github.com/vllm-project/vllm/commit/e0317b28ce3ba4c9bd2ff69d885e3f34688a6d71)

- **作者**: Matt
- **时间**: 2026-10-12T15:53:26Z
- **提交信息**: [Feature] Support batch invariance on ROCm (#52231)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [50b21a2](https://github.com/vllm-project/vllm/commit/50b21a2667b6903d2e0d651aab9f449832e5e1e9)

- **作者**: TJian
- **时间**: 2026-10-12T15:50:28Z
- **提交信息**: [Perf] [Feat] [ROCm] Add densemha support to ROCm AITER Sparse MLA (#49263)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [a686c8e](https://github.com/vllm-project/vllm/commit/a686c8e1b7e5870eadfc9f47447de2b8a26211fc)

- **作者**: Nick Riasanovsky
- **时间**: 2026-10-12T15:38:43Z
- **提交信息**: [Triton] Migrate Triton kernels off tl.make_block_ptr for triton-main compat (#60502)

Signed-off-by: Nick Riasanovsky <njriasan@meta.com>

### [ffec221](https://github.com/vllm-project/vllm/commit/ffec221276fa39d7927b9bb63dc12766d77fc403)

- **作者**: Shang Wang
- **时间**: 2026-10-12T14:23:00Z
- **提交信息**: [Bugfix][DSv4.1] Match decoder-replay input_ids dtype for FlashInfer MegaMoE (#61041)

Signed-off-by: Shang Wang <samshang.wang@mail.utoronto.ca>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f3cb10b](https://github.com/vllm-project/vllm/commit/f3cb10b690c352265048991901de0e62b65abe8c)

- **作者**: Hoai Vo
- **时间**: 2026-10-12T14:09:53Z
- **提交信息**: [Model][LoRA] Enable LoRA support for BERT and RoBERTa embedding models (#61033)

Signed-off-by: hoaivoke <vokehoai@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [716961c](https://github.com/vllm-project/vllm/commit/716961cf1fc474c491d401adece882af3b39d5ab)

- **作者**: Shang Wang
- **时间**: 2026-10-12T14:05:09Z
- **提交信息**: [Bugfix] Drop enable_in_kernel_fc2_reduce from FlashInfer CuteDSL MegaMoE config (#59900)

Signed-off-by: Shang Wang <samshang.wang@mail.utoronto.ca>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a281ad3](https://github.com/vllm-project/vllm/commit/a281ad32f0368caa2c6ebe38a0e59a75b3f22392)

- **作者**: Ilya Markov
- **时间**: 2026-10-12T14:03:09Z
- **提交信息**: [EPLB] Add EPLB support to dspark draft models (DeepSeekV4) (#57549)

Signed-off-by: Markov Ilya <markovilya197@gmail.com>

### [b3ee560](https://github.com/vllm-project/vllm/commit/b3ee560ae816b763b09b1aeddf9adca95a0014d0)

- **作者**: Ilya Markov
- **时间**: 2026-10-12T14:02:56Z
- **提交信息**: [Bugfix][MoE] Apply expert_map remapping for CUTLASS FP4 MOE expert parallel (#59042)

Signed-off-by: Markov Ilya <markovilya197@gmail.com>

### [f022975](https://github.com/vllm-project/vllm/commit/f022975964e27ed18dd8e437eed0ab70b0a00b33)

- **作者**: bzsuni
- **时间**: 2026-10-12T13:49:46Z
- **提交信息**: [Bugfix] Reject beam search in completion render (#61212)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>

### [4c36d21](https://github.com/vllm-project/vllm/commit/4c36d21280824d1a9c521106932408243078de0d)

- **作者**: Suraj Sharan
- **时间**: 2026-10-12T13:49:30Z
- **提交信息**: [Bugfix][LoRA] Apply PEFT rank_pattern / alpha_pattern scaling per module (#59801)

Signed-off-by: suraj <surajsharan85@gmail.com>
Co-authored-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>
Co-authored-by: linitra24 <renshuang.zhou@daocloud.io>

### [3facf82](https://github.com/vllm-project/vllm/commit/3facf822b771cc0a47a346249d6ea42f9071aaac)

- **作者**: Harry Mellor
- **时间**: 2026-10-12T13:45:54Z
- **提交信息**: [Performance] Load HF tokenizers and processors from a local snapshot (#60825)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [092c35d](https://github.com/vllm-project/vllm/commit/092c35dd155db2644da6bb671332c51902bd3039)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-12T13:27:34Z
- **提交信息**: [Model] Support Cloudflare/clef-omni on /v1/systemone (#61064)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [314ab8c](https://github.com/vllm-project/vllm/commit/314ab8cffd9b115198d50491c5f1c4a2112ad4a1)

- **作者**: DimensionSTP
- **时间**: 2026-10-12T13:25:36Z
- **提交信息**: [Bugfix][Structured Output] Drain compilation tasks before releasing the backend (#61047)

Signed-off-by: DimensionSTP <65501090+DimensionSTP@users.noreply.github.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [ac28877](https://github.com/vllm-project/vllm/commit/ac28877f0e86452f2e151279bdc373cd58ae88f0)

- **作者**: Chauncey
- **时间**: 2026-10-12T13:21:35Z
- **提交信息**: [Bugfix] Fix out-of-bounds lookahead in adaptive block verification (#60945)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [8c175f4](https://github.com/vllm-project/vllm/commit/8c175f403acd2749086c298cd1c6f29ed9b4e2ba)

- **作者**: stefankoncarevic
- **时间**: 2026-10-12T13:20:35Z
- **提交信息**: [CI][ROCm] Compare greedy output only in the AITER attn+quant test (#61185)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [7900d2e](https://github.com/vllm-project/vllm/commit/7900d2eabc4f9a7facb7a196a04c2c32803a79c8)

- **作者**: Rohan Potdar
- **时间**: 2026-10-12T13:18:44Z
- **提交信息**: [Test] Accept tied tokens at the k-th value in the Triton top-k test (#60726)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c75cb63](https://github.com/vllm-project/vllm/commit/c75cb63cd2bb8e0dc62608e9930d8b953ee3b422)

- **作者**: Harry Huang
- **时间**: 2026-10-12T12:56:44Z
- **提交信息**: [Qwen4Exp] support Sequence Parallelism for Qwen3.8-Flash-Next (#56322)

Signed-off-by: huanghaoyan.hhy <huanghaoyan.hhy@alibaba-inc.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [258b97f](https://github.com/vllm-project/vllm/commit/258b97ff6bc1dbbc7b76d2d5a5a87591f9de107f)

- **作者**: Tianyu Guo
- **时间**: 2026-10-12T12:32:39Z
- **提交信息**: [Bugfix][EC Connector] Size transfers by measured encoder output widths (#57904)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>

### [aa1d44d](https://github.com/vllm-project/vllm/commit/aa1d44df16fe554405c6064cad2a904a16b63581)

- **作者**: Liana Koleva
- **时间**: 2026-10-12T12:20:53Z
- **提交信息**: [Bugfix][Rust Frontend] Alias `qwen3_xml` to `qwen3_coder` and add `qwen3_json` for the Qwen JSON format (#60136)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [8d7b93f](https://github.com/vllm-project/vllm/commit/8d7b93fec2eb72ce01f2217472ac1f51b9bce600)

- **作者**: Shimi Bandiel
- **时间**: 2026-10-12T11:37:53Z
- **提交信息**: [Frontend] Report stop_reason on /inference/v1/generate and pass it through derender (#60251)

Signed-off-by: Hyeonki Hong <hhk7734@gmail.com>
Signed-off-by: Shimi Bandiel <shimib@google.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Hyeonki Hong <hhk7734@gmail.com>
Co-authored-by: Mimir <mimir@nousresearch.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [32b05ad](https://github.com/vllm-project/vllm/commit/32b05addc1301be904ba1b6c9a5e3704581b1fc3)

- **作者**: Reid
- **时间**: 2026-10-12T11:12:43Z
- **提交信息**: [Bugfix][Rust Frontend] Restore DP wave delivery after XPUB reconnects (#60249)

Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f5cda48](https://github.com/vllm-project/vllm/commit/f5cda48c9023e8ea3b5d29b57815c8455473e97b)

- **作者**: Reid
- **时间**: 2026-10-12T11:12:39Z
- **提交信息**: [Bugfix][Rust Frontend] Export corrupted request metric (#59937)

Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [3b9e462](https://github.com/vllm-project/vllm/commit/3b9e46277407ed53317e78114ad50f1f9bd9d6a4)

- **作者**: 0xsensei
- **时间**: 2026-10-12T11:12:35Z
- **提交信息**: [Bugfix][Rust Frontend] Correct DP routing after request removal (#59631)

Signed-off-by: 0xsensei <prblmslvr.aditya@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2144580](https://github.com/vllm-project/vllm/commit/21445806bdf6cfc4fdb9b161643e081bd73cc716)

- **作者**: Zupeng Wang
- **时间**: 2026-10-12T11:12:30Z
- **提交信息**: [Rust Frontend] Support logprob_token_ids on OpenAI endpoints (#59549)

Signed-off-by: Wang Zupeng <zupenwang@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ee8f7ea](https://github.com/vllm-project/vllm/commit/ee8f7ea4493bf95e7c04951aec701af4000abdb7)

- **作者**: Thang Nguyen
- **时间**: 2026-10-12T10:46:07Z
- **提交信息**: [CI] Enroll a fourth batch of five steps in automatic sharding (#60858)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f7a3a72](https://github.com/vllm-project/vllm/commit/f7a3a7265f5161594721e8c1aa6b68a761629b68)

- **作者**: MatthewCYM
- **时间**: 2026-10-12T10:42:51Z
- **提交信息**: [Bugfix][Multimodal] Fix Qwen3-ASR audio preprocessing parity (#57146)

Signed-off-by: MatthewCYM <chenyiming0v0@gmail.com>

### [2534a96](https://github.com/vllm-project/vllm/commit/2534a96fcf165202f5358335f8b0705175159fd0)

- **作者**: Jimmy Wang
- **时间**: 2026-10-12T09:47:52Z
- **提交信息**: [Docs] List additional unauthenticated endpoints (#61081)

Signed-off-by: Jimmy Wang <53066820+JimmyWang0417@users.noreply.github.com>
Co-authored-by: Juan Pérez de Algaba <124347725+jperezdealgaba@users.noreply.github.com>

### [5a09062](https://github.com/vllm-project/vllm/commit/5a0906263209da2c1165ce82b9fe8e767aa89669)

- **作者**: Bugen Zhao
- **时间**: 2026-10-12T09:43:48Z
- **提交信息**: [Rust Frontend] Compose answer constraints into parser-owned output grammars (#60781)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0466bd3](https://github.com/vllm-project/vllm/commit/0466bd36ea9f6300acbc15c705b1ebe61590c691)

- **作者**: Bugen Zhao
- **时间**: 2026-10-12T09:43:47Z
- **提交信息**: [Rust Frontend] Build the Kimi K3 full-output grammar from its parser mode (#59190)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [83773ec](https://github.com/vllm-project/vllm/commit/83773ecdf3ce6da9a2f2bd14cb87e6bbf58d4229)

- **作者**: Shijin Zhang
- **时间**: 2026-10-12T09:22:55Z
- **提交信息**: [Frontend] Support CustomToolCall in the non-Harmony Responses API (#57322)

Signed-off-by: Shijin Zhang <75300765+Dovis01@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [a33d46b](https://github.com/vllm-project/vllm/commit/a33d46b47193e3273dc38f980abbf55459f3c77f)

- **作者**: zhangchengzhucufe-dev
- **时间**: 2026-10-12T09:10:55Z
- **提交信息**: [Bugfix][XPU] Forward softcap and alibi_slopes in xpu_ops.flash_attn_varlen_func (#58936)

Signed-off-by: zhangchengzhucufe-dev <zhangchengzhucufe@gmail.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [e05201a](https://github.com/vllm-project/vllm/commit/e05201aa2e5ccf19284e5062064050a06d50e281)

- **作者**: Yan Ma
- **时间**: 2026-10-12T08:59:38Z
- **提交信息**: [XPU] refine memory release for sleep mode (#61158)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [99b44c7](https://github.com/vllm-project/vllm/commit/99b44c7a4282e903edc0c4703f50d3a72f4d419b)

- **作者**: Thuongvu Ho
- **时间**: 2026-10-12T08:31:07Z
- **提交信息**: [Metrics] Add admission rejection metrics (#55812)

Signed-off-by: Thuongvu Ho <thuongvuho@gmail.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [5bed289](https://github.com/vllm-project/vllm/commit/5bed289707f3b647c903eb6911a2ca6e20ebf74c)

- **作者**: Cyrus Leung
- **时间**: 2026-10-12T08:06:47Z
- **提交信息**: [DX] Update CODEOWNERS for entrypoints (#60984)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [4163a80](https://github.com/vllm-project/vllm/commit/4163a80142d41b98f94d9b798506448162a22407)

- **作者**: Shuolei Wang
- **时间**: 2026-10-12T07:56:59Z
- **提交信息**: [Rust Frontend] Return weight-version spans on final outputs (#61070)

Signed-off-by: Shuolei Wang <shuoleiwang123@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f4114e0](https://github.com/vllm-project/vllm/commit/f4114e068e5d8e961defeb7747a9449d5eec0659)

- **作者**: Ting SUN
- **时间**: 2026-10-12T07:55:06Z
- **提交信息**: [Bugfix][Frontend] Preserve token IDs in chat derender responses (#61065)

Signed-off-by: Ting Sun <suntcrick@gmail.com>

### [e3bbaf2](https://github.com/vllm-project/vllm/commit/e3bbaf23695f7f30f144a288057b0419ab2b6a8d)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-12T07:53:16Z
- **提交信息**: [ROCm][DSv4] Fuse the shared expert into AITER MegaMoE (#61004)

Signed-off-by: Yanfei Wang <yanfei.wang@amd.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [36f3972](https://github.com/vllm-project/vllm/commit/36f397281295f5b58852a7eaf429b90348161079)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-12T07:09:10Z
- **提交信息**: [Spec Decode] Skip metadata build for dflash/dspark when all model backends support it (#60692)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: Rishi Puri <20074092+puririshi98@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-13
**监控日期**: 2026-10-12
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7140
- **最后更新**: 2026-10-13T02:22:29Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 11
- **主要提交者**: Clodagh Walsh, wangzhao-11a, lazariv

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本次提交以 **Bug 修复为主（8/11）**，辅以 **性能优化（1）**、**文档更新（1）** 和 **功能增强（1）**。这是一个典型的稳定性和质量提升批次，而非功能推进阶段。

### 2. 关键变更点及与项目方向的关系

- **多模态全栈适配**：修复涵盖语音合成（CosyVoice3、MOSS-TTS、SeedVR2）、实时对话（Realtime WebSocket）、双工通信（Duplex）等多个模态模块，体现 vllm-omni 作为全模态推理引擎的广度。

- **NPU 硬件生态持续投入**：4 条提交涉及 NPU（约 36%），包括 profiler 参数透传和 K/V 缓存分配保序，说明华为 NPU 支持是当前重点方向。

- **MiniCPM-o 跨硬件图共享**：将 Code2Wav 图结构在 CUDA 和 NPU 间共享，直接服务于"cheap serving"的项目目标，减少硬件切换的重复开发成本。

- **实时语音链路加固**：session.update 时序修复、WebSocket 嵌套错误码读取修复、双工流式上下文溢出后副本存活修复，三条提交集中打磨 Realtime/Duplex 场景的健壮性，表明该场景已进入生产级打磨阶段。

### 3. 对项目的影响和潜在意义

- **稳定性提升**：FP16 溢出预防（SeedVR2 RMSNorm）和权重迭代器修正（CosyVoice3）等修复降低了极端场景下的崩溃风险，对在线服务可靠性有直接贡献。
- **可观测性增强**：NPU profiler 参数透传使性能分析工具链在 NPU 上与 CUDA 对齐，降低调试门槛。
- **社区运营**：更新微信 QR 码和 OmniVoice 指令校验，体现中国社区活跃度和对易用性的关注。

### 4. 值得关注的技术点

- **跨硬件图复用（CUDA↔NPU）**：MiniCPM-o 的 Code2Wav 图共享是一种架构层面的抽象优化，值得其他 omni 模型跟进。
- **双工流式上下文溢出后的副本保活**：涉及分布式推理中的容错语义，修复难度和影响面较高。
- **Cursor AI 协作开发**：出现 Cursor Agent 作为共同作者，反映项目已引入 AI 辅助编码工作流。

### 5. 对项目发展的整体影响

vllm-omni 的目标是"Easy, fast, and cheap omni-modality model serving"。本批次提交集中体现了对 **"Easy"（稳定易用）** 和 **"Cheap"（跨硬件高效）** 两个维度的持续打磨。在 NPU 生态的深入投入与跨硬件抽象的建立，为项目在异构硬件环境中的部署广度奠定基础。实时语音链路的密集修复则表明该项目正从功能搭建阶段转向生产可用阶段，是走向成熟的关键信号。

## 详细提交记录

### [76f52f1](https://github.com/vllm-project/vllm-omni/commit/76f52f1ae59078cecf47759a56d73e8bcd2ba311)

- **作者**: lazariv
- **时间**: 2026-10-12T16:36:52Z
- **提交信息**: [Bugfix] Realtime: reply to session.update before any other event (#8839)

Signed-off-by: lazariv <lazariv.taras@gmail.com>

### [4eb53e1](https://github.com/vllm-project/vllm-omni/commit/4eb53e137c7d140a78b4c484b1e9872fb24b7697)

- **作者**: Yueqian Lin
- **时间**: 2026-10-12T16:34:56Z
- **提交信息**: [BugFix] CosyVoice3: honor the weights iterator in load_weights (#6738)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [744d6da](https://github.com/vllm-project/vllm-omni/commit/744d6dae9d7e9b718ea2ff93a62dccc240f93cd6)

- **作者**: wangzhao-11a
- **时间**: 2026-10-12T15:17:32Z
- **提交信息**: [Bugfix][NPU] Forward torch_profiler_record_shapes to the NPU profiler (#8770)

Signed-off-by: wangzhao-11a <2638825065@qq.com>

### [fdb41eb](https://github.com/vllm-project/vllm-omni/commit/fdb41ebf255b2568988f64daff07527186b6c108)

- **作者**: Weiming Liao
- **时间**: 2026-10-12T15:03:56Z
- **提交信息**: [Bugfix][NPU] Preserve contiguous K/V cache allocation (#8827)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [0708f05](https://github.com/vllm-project/vllm-omni/commit/0708f05e2e27f16fca8b48e7c5a085277d1cafda)

- **作者**: 汪志鹏
- **时间**: 2026-10-12T14:57:10Z
- **提交信息**: [Bugfix] Prevent FP16 overflow in SeedVR2 RMSNorm (#8767)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [c124d02](https://github.com/vllm-project/vllm-omni/commit/c124d02168337ef329d8b00933fad80c02fb5c7e)

- **作者**: amy-why-3459
- **时间**: 2026-10-12T14:01:41Z
- **提交信息**: [Perf][MiniCPM-o] Share Code2Wav graphs across CUDA and NPU (#8735)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [74ba8ab](https://github.com/vllm-project/vllm-omni/commit/74ba8ab6927552e82688459c8015330245c81c1a)

- **作者**: wangyu
- **时间**: 2026-10-12T10:59:49Z
- **提交信息**: [Bugfix] Read nested Realtime WebSocket error codes in tests (#8825)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [c101150](https://github.com/vllm-project/vllm-omni/commit/c10115052ef691e4d0270f1ddf5bce5bc4d140f8)

- **作者**: NATURE
- **时间**: 2026-10-12T09:17:14Z
- **提交信息**: [Bugfix][Duplex] Keep replicas alive after streaming context overflow [fix personaPlex stage 0 crash bug] (#8683)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [156ddb3](https://github.com/vllm-project/vllm-omni/commit/156ddb3f4afc25a6bc0fbeffea3170ebdc443db8)

- **作者**: WeiQing Chen
- **时间**: 2026-10-12T08:48:14Z
- **提交信息**: [Doc] Update vLLM-Omni WeChat QR code (#8806)

Signed-off-by: David Chen <530634352@qq.com>

### [e2450fd](https://github.com/vllm-project/vllm-omni/commit/e2450fd6fa735c6fb970d04730b004ed89e44e4f)

- **作者**: Clodagh Walsh
- **时间**: 2026-10-12T08:23:31Z
- **提交信息**: OmniVoice: Validate instructions  (#6105)

Signed-off-by: Clodagh Walsh <clodaghwalsh17@gmail.com>

### [6fac3e5](https://github.com/vllm-project/vllm-omni/commit/6fac3e5fcbac7005f127ae9d562a3c5fbf400a37)

- **作者**: Sy03
- **时间**: 2026-10-12T08:17:34Z
- **提交信息**: [Core] Reduce MOSS-TTS Local serving overhead (#8667)

Signed-off-by: Sy03 <1370724210@qq.com>
Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>

---
