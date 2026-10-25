# GitHub Stars 合并报告 - 2026-10-24

**合并日期**: 2026-10-25
**监控日期**: 2026-10-24
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


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2264
- **最后更新**: 2026-10-24T00:29:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2953
- **最后更新**: 2026-10-24T18:22:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2312
- **最后更新**: 2026-10-23T16:51:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6774
- **最后更新**: 2026-10-25T00:11:41Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 2
- **主要提交者**: Yang Xu, eigen

## AI分析总结

# FlashInfer 昨日 26 提交合并总结

## 一、主要更新类型
以**性能优化**为绝对主线（约 2/3 提交），辅以**功能新增**（新硬件支持、量化格式扩展、训练算子）、少量 **Bug 修复**与代码重构，以及 1 条文档/基准数据更新。

## 二、关键变更点

**1. Cake 后端内核持续微调**：cake_qsa_nvfp4 将 E4M3 block scale 的 rebias 折叠进 E2M1 查找表并常驻寄存器；cake_nvfp4_svdquant 引入 256 字节 L2 line promotion 的 TMA 加载；cake_vsa_sm90 将 FP8 转置交接的 V^T 分块从 2 块提到 8 块；GDP 解码将行加载提前到 k 加载点重叠访存、split-V 状态改为 128 位全局内存直读入寄存器（共享内存从 6400 降到 2048 字节级），输出逐位一致。

**2. MoE 推理两条技术路线并进**：Frost（cuTile 框架）低延迟路径一次性铺开 NVFP4/MXFP4/MXINT4 四位权重格式，随后扩展 FP16 输入输出、PowLU 激活与 SM120 W8 路由复用；同时新增 Hopper SM90 与 SM120 上分组 BF16 Tensor Core MoE decode kernel（多路由同专家时按组加载权重，H100 上相比 FMA 路径 1.25–1.27×，部分场景较 TRT-llm 达 2.5–4.7×）。

**3. 硬件代际全面铺开**：面向 Hopper（sm_90a）→ Blackwell（sm_100a/103a）→ Rubin（sm_107a，即 R200）三代 GPU，包括 fused RMSNorm 新增 sm_107a 后端、KDA 上下文并行与调度优化、mHC 训练算子（R200 前向提速 1.17×）、GQA 稀疏注意力 40 个新程序等。

**4. 训练侧延伸**：GDN 上下文并行训练内核（相对 FLA 基线 2.8–3.9×），KDA 前向/反向/checkpoint 重放路径调优——项目正从纯推理算子库向训练场景拓展。

**5. 修复与清理**：修正 sm_107a 构建清单 min_cuda 提至 13.4；修复 SM120 W4A16 直接路由 CUDA Graph capture 的 scratch 越界；修复 cuTile int64 宽索引与 int32 归纳变量类型不匹配；删除 117 条冗余显式模板实例化（274 行）并验证 SASS 逐字节一致。

## 三、项目影响
用户可见 API 基本不变，属于"静默"性能收益，下游 LLM 部署可直接受益；新硬件与新工具链覆盖巩固了 FlashInfer 作为主流推理加速库的生态地位；DSA indexer 翻倍 persistent workspace 换取 1.16× 提速的策略表明项目接受以显存换速度的权衡。

## 四、值得关注的技术点
- 查找表折叠加字节 permute 生成 PV scale，位级一致下获 2–3% 提速；
- BF16x3 半宽张量核乘积模拟 FP32，绕过 TF32 精度限制；
- SM107 上关闭 L2 prefetch/evict-first 提示反而更快，揭示新架构内存层级差异；
- GQA 内核按查询头/ KV 头区分量化的精细工程化；
- DSA indexer 新增 far_sample 参数，attention-sink 场景最高 1.35×。

## 五、整体发展影响
FlashInfer 正从"注意力内核集合"演进为**覆盖推理与训练、跨三代 NVIDIA 架构、多量化格式的完整 GPU 算子基础设施**。Cake 与 Frost 双栈并行、对 cuDNN/CUTLASS/TRT-LLM 的对标测量、逐位一致验证与诚实报告性能回退的工程文化，共同构筑了项目的技术护城河与可信度标杆。

## 详细提交记录

### [0fac207](https://github.com/flashinfer-ai/flashinfer/commit/0fac207b466d494270f27d5cf738c172aed8f4a9)

- **作者**: eigen
- **时间**: 2026-10-24T23:51:37Z
- **提交信息**: fix(cake_muse_spark_norm, cake_tp_moe_finalize_rmsnorm): raise the sm_107a min_cuda floor to 13.4 (#7199)

This PR fixes the toolkit floor for the `sm_107a` entries in two Cake
build manifests. `cake_build.jit_specs` and
`scripts/check_cake_build_manifests.py` use the per-entry `min_cuda`
value to skip any entry the local toolkit can't build ("skip min_cuda >
toolkit"). These entries had `"min_cuda": "13.0"`, so a CUDA 13.0–13.3
toolkit kept them. nvcc then failed on
`-gencode=arch=compute_107a,code=sm_107a` with a raw `nvcc fatal :
Unsupported gpu architecture 'compute_107a'` instead of the intended
"needs CUDA 13.4 or newer" message. CodeRabbit flagged this on #7173.

The PR changes `"min_cuda": "13.0"` to `"min_cuda": "13.4"` for the 35
`sm_107a` entries in
`flashinfer/cake_muse_spark_norm_backend/build.json` and the 6 `sm_107a`
entries in `flashinfer/cake_tp_moe_finalize_rmsnorm_backend/build.json`.
With this floor, a CUDA 13.0–13.3 toolkit skips these entries through
the `min_cuda` check, so the build no longer hits the raw nvcc error.
Nothing else changes. No kernel source or host code is touched.
`common.requires.cuda_toolkit.min` stays 12.8 in both manifests because
it is the lowest entry floor of a package. The sm_100a and sm_103a
entries keep 12.8 / 12.9. The kernels, routes and measured speedups of
#7120, #7173, #7119 and #7177 are unchanged. On a CUDA 13.4+ toolkit,
nothing changes.

nvcc supports `compute_107a` / `sm_107a` starting with CUDA 13.4. The
CUDA 13.4 nvcc documentation lists them ("Rubin support"), and no
13.0–13.3.1 edition does. Confirmed by compiling a trivial kernel with
`-gencode=arch=compute_107a,code=sm_107a -cubin` using the pip
toolchains (`nvidia-cuda-nvcc` and companions pinned per release); as a
control, `sm_103a` compiled on every release.

| nvcc | `sm_107a` |
|---|---|
| 13.0.88 | rejected: Unsupported gpu architecture 'compute_107a' |
| 13.1.115 | rejected |
| 13.2.86 | rejected |
| 13.3.73 | rejected |
| 13.4.59 | compiles |
| 13.4.92 | compiles |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* The minimum CUDA version for select `sm_107a` builds is now 13.4.
Other architecture builds and library metadata are unchanged. This may
affect compatibility when using those builds with older CUDA versions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [cb93a30](https://github.com/flashinfer-ai/flashinfer/commit/cb93a30db500810a8be64fb45a1cc1c26eff0770)

- **作者**: eigen
- **时间**: 2026-10-24T23:43:46Z
- **提交信息**: perf(cake_qsa_nvfp4): fold the block-scale rebias into the E2M1 tables and hold the table words per tile (#7175)

The kernel is gated sparse paged GQA decode attention over an NVFP4
(E2M1) KV cache with E4M3 block scales, BF16 queries and 256-dim heads.
One data-type variant serves the NHD and HND layouts in two forms: split
(decode + merge) and a fused co-resident decode on sm_90a. That makes
four programs in all: the K-first decode (sm_80 and sm_90a), the
cooperative fused decode (sm_90a), the sm_80 whole-tile decode, and the
merge. This PR changes the NVFP4 dequant of the decode programs in three
ways: it folds the E4M3 block scale's rebias multiply into the E2M1
magnitude tables, keeps the two table words in registers for the tile,
and forms the PV scale words from the token pair's two scale bytes with
one byte permute (on sm_80 the last two apply to the whole-tile program
only); outputs are bitwise identical to the package before this PR.
Compared with the package before this PR (previous), on H100 the whole
call is 1.019x-1.036x faster at rows 4-8 under both flush modes and
within noise (0.996x-1.009x) at rows 16-128. On A100 80GB the 128-row
calls are 1.025x (NHD) and 1.016x (HND) faster under the read flush and
1.012x / 1.010x under the memset flush, and rows 1-64 are within noise
(0.985x-1.007x; the NHD rows-64 read-flush row reads 0.985x and is
reported as measured). Rows 1-2 on H100 carry the harness's known order
effect (their two directional ratios disagree), so their 1.05x-1.07x is
reported as measured, not as a claim.

NVIDIA H100 80GB HBM3 (sm_90a, 132 SMs), PyTorch 2.14.1+cu130 (CUDA 13.0
runtime), kernels JIT-built with nvcc 13.4: GPU-event time of the whole
call through the package entry (per-call workspace), 24 x 2 heads, top-k
2051 (33 tiles), a memset L2 flush before every call, 3 groups x 64
iterations; speedup = previous / this PR.

| layout | rows | previous (us) | this PR (us) | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 10.02 | 9.36 | 1.070x |
| NHD | 2 | 11.20 | 10.62 | 1.054x |
| NHD | 4 | 12.72 | 12.45 | 1.022x |
| NHD | 8 | 16.43 | 16.02 | 1.026x |
| NHD | 16 | 22.08 | 22.06 | 1.001x |
| NHD | 32 | 32.58 | 32.38 | 1.006x |
| NHD | 64 | 56.24 | 56.42 | 0.997x |
| NHD | 128 | 99.66 | 99.04 | 1.006x |
| HND | 1 | 9.73 | 9.07 | 1.072x |
| HND | 2 | 10.91 | 10.38 | 1.051x |
| HND | 4 | 12.30 | 12.02 | 1.024x |
| HND | 8 | 16.53 | 16.22 | 1.019x |
| HND | 16 | 22.96 | 22.96 | 1.000x |
| HND | 32 | 34.59 | 34.34 | 1.007x |
| HND | 64 | 59.33 | 58.93 | 1.007x |
| HND | 128 | 102.81 | 102.86 | 1.000x |

NVIDIA H100 80GB HBM3 (sm_90a, 132 SMs), PyTorch 2.14.1+cu130 (CUDA 13.0
runtime), kernels JIT-built with nvcc 13.4: GPU-event time of the whole
call through the package entry (per-call workspace), 24 x 2 heads, top-k
2051 (33 tiles), a read L2 flush before every call, 3 groups x 64
iterations; speedup = previous / this PR.

| layout | rows | previous (us) | this PR (us) | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 9.52 | 8.90 | 1.070x |
| NHD | 2 | 10.62 | 9.94 | 1.069x |
| NHD | 4 | 11.76 | 11.50 | 1.022x |
| NHD | 8 | 15.58 | 15.20 | 1.025x |
| NHD | 16 | 20.85 | 20.66 | 1.009x |
| NHD | 32 | 30.78 | 30.75 | 1.001x |
| NHD | 64 | 52.16 | 52.16 | 1.000x |
| NHD | 128 | 92.70 | 92.86 | 0.998x |
| HND | 1 | 9.54 | 8.93 | 1.068x |
| HND | 2 | 10.74 | 10.08 | 1.065x |
| HND | 4 | 11.90 | 11.66 | 1.021x |
| HND | 8 | 15.68 | 15.14 | 1.036x |
| HND | 16 | 21.01 | 20.94 | 1.003x |
| HND | 32 | 31.54 | 31.38 | 1.005x |
| HND | 64 | 53.36 | 53.15 | 1.004x |
| HND | 128 | 92.61 | 93.01 | 0.996x |

NVIDIA A100 80GB PCIe (sm_80, 108 SMs), PyTorch 2.14.1+cu130 (CUDA 13.0
runtime), kernels JIT-built with nvcc 13.4: GPU-event time of the whole
call through the package entry (per-call workspace), 24 x 2 heads, top-k
2051 (33 tiles), a memset L2 flush before every call, 3 groups x 64
iterations; speedup = previous / this PR.

| layout | rows | previous (us) | this PR (us) | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 14.88 | 14.85 | 1.002x |
| NHD | 2 | 17.94 | 17.81 | 1.007x |
| NHD | 4 | 21.09 | 21.04 | 1.002x |
| NHD | 8 | 25.42 | 25.55 | 0.995x |
| NHD | 16 | 35.34 | 35.22 | 1.004x |
| NHD | 32 | 56.46 | 56.30 | 1.003x |
| NHD | 64 | 109.26 | 109.34 | 0.999x |
| NHD | 128 | 182.80 | 180.56 | 1.012x |
| HND | 1 | 15.34 | 15.36 | 0.999x |
| HND | 2 | 18.42 | 18.37 | 1.003x |
| HND | 4 | 21.66 | 21.68 | 0.999x |
| HND | 8 | 26.24 | 26.08 | 1.006x |
| HND | 16 | 37.26 | 37.26 | 1.000x |
| HND | 32 | 59.07 | 58.75 | 1.005x |
| HND | 64 | 110.93 | 111.19 | 0.998x |
| HND | 128 | 186.11 | 184.32 | 1.010x |

NVIDIA A100 80GB PCIe (sm_80, 108 SMs), PyTorch 2.14.1+cu130 (CUDA 13.0
runtime), kernels JIT-built with nvcc 13.4: GPU-event time of the whole
call through the package entry (per-call workspace), 24 x 2 heads, top-k
2051 (33 tiles), a read L2 flush before every call, 3 groups x 64
iterations; speedup = previous / this PR.

| layout | rows | previous (us) | this PR (us) | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 14.19 | 14.21 | 0.999x |
| NHD | 2 | 16.83 | 16.77 | 1.004x |
| NHD | 4 | 19.54 | 19.57 | 0.998x |
| NHD | 8 | 24.06 | 23.95 | 1.005x |
| NHD | 16 | 32.98 | 32.80 | 1.005x |
| NHD | 32 | 51.74 | 51.55 | 1.004x |
| NHD | 64 | 92.05 | 93.47 | 0.985x |
| NHD | 128 | 174.07 | 169.81 | 1.025x |
| HND | 1 | 14.59 | 14.72 | 0.991x |
| HND | 2 | 17.02 | 16.99 | 1.002x |
| HND | 4 | 19.90 | 19.86 | 1.002x |
| HND | 8 | 24.43 | 24.29 | 1.006x |
| HND | 16 | 33.33 | 33.38 | 0.999x |
| HND | 32 | 52.14 | 52.02 | 1.002x |
| HND | 64 | 96.27 | 95.89 | 1.004x |
| HND | 128 | 174.99 | 172.16 | 1.016x |

The merge program is unchanged, and the kernel family's single data-type
variant ships on sm_80 and sm_90a, so the H100 (sm_90a) and A100 (sm_80)
measurements above cover both layouts on both architectures.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Added input validation for page division values, query/output head
counts, and head strides. Invalid values are now rejected before
processing.
* Tightened integer-bound comparisons for several parameters while
preserving their existing accepted limits.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [26d0d5d](https://github.com/flashinfer-ai/flashinfer/commit/26d0d5dc906ca3738d02d796a7c71faf6952f690)

- **作者**: eigen
- **时间**: 2026-10-24T23:37:10Z
- **提交信息**: perf(cake_mhc): faster four-stream mHC (hidden size 4096) with grad on SM100 / SM103 / SM107 (#7198)

This PR replaces the Cake mHC (manifold-constrained hyper-connections)
training kernels added in #6897 as `flashinfer.cake_mhc_train` with
faster forms of the same kernels. The public API, the autograd boundary
and the saved statistics (256 B/token) are unchanged. As in #6897, this
is the only mHC training variant Cake ships: four residual streams at
hidden size 4096 (the GLM-5.3-Flash configuration), with the token count
T as a runtime value, BF16 activations at the API boundaries, and the
mapping GEMM, the Sinkhorn coefficients and the parameter gradients in
FP32. The kernels cover three paths: forward; backward, which is first
order and computes dX, dB and the FP32 parameter gradients from the
saved statistics; and checkpoint, which recomputes the forward and runs
the backward with nothing saved. The baseline is the previous Cake
version (#6897), measured in paired runs in the same process and on the
same inputs as this PR's kernels, using kernel time per call. Each GPU
was measured in two independent sessions at 13 token counts from 1024 to
65536; the speedup is the previous version's kernel time divided by this
PR's, and the ranges below cover both sessions and all token counts. On
GB300 (sm_103a) the speedup is 1.02x to 1.05x for forward, 1.05x to
1.17x for backward and 1.06x to 1.15x for checkpoint. On B200 (sm_100a)
it is 1.02x to 1.04x for forward, 1.05x to 1.13x for backward and 1.07x
to 1.12x for checkpoint, and on R200 (sm_107a) it is 1.10x to 1.17x for
forward, 1.02x to 1.13x for backward and 1.03x to 1.12x for checkpoint.

**NVIDIA GB300 (sm_103a), CUDA 13.4; kernel time per call in
microseconds, median of paired runs; two independent sessions (1 / 2);
speedup = previous / this PR**

| T (tokens) | Path | Previous (µs), session 1 | This PR (µs), session 1
| Speedup, session 1 | Previous (µs), session 2 | This PR (µs), session
2 | Speedup, session 2 |
|---:|---|---:|---:|---:|---:|---:|---:|
| 1024 | forward | 41.6 | 39.9 | 1.04x | 41.5 | 39.8 | 1.04x |
| 1024 | backward | 75.8 | 66.1 | 1.15x | 75.5 | 65.9 | 1.15x |
| 1024 | checkpoint | 94.8 | 83.5 | 1.14x | 94.3 | 83.2 | 1.13x |
| 4096 | forward | 107.9 | 106.3 | 1.02x | 107.7 | 106.1 | 1.02x |
| 4096 | backward | 222.4 | 190.3 | 1.17x | 221.5 | 189.4 | 1.17x |
| 4096 | checkpoint | 258.5 | 225.0 | 1.15x | 257.3 | 223.7 | 1.15x |
| 8192 | forward | 203.0 | 195.1 | 1.04x | 203.4 | 195.0 | 1.04x |
| 8192 | backward | 360.7 | 328.7 | 1.10x | 359.6 | 327.9 | 1.10x |
| 8192 | checkpoint | 426.4 | 387.2 | 1.10x | 425.4 | 386.1 | 1.10x |
| 14928 | forward | 357.6 | 342.3 | 1.04x | 356.2 | 341.9 | 1.04x |
| 14928 | backward | 607.7 | 563.5 | 1.08x | 605.8 | 563.1 | 1.08x |
| 14928 | checkpoint | 720.7 | 661.9 | 1.09x | 717.5 | 660.5 | 1.09x |
| 15288 | forward | 364.9 | 348.6 | 1.05x | 361.8 | 348.5 | 1.04x |
| 15288 | backward | 619.8 | 577.1 | 1.07x | 619.3 | 576.3 | 1.07x |
| 15288 | checkpoint | 734.5 | 675.8 | 1.09x | 730.7 | 674.6 | 1.08x |
| 15566 | forward | 370.0 | 353.4 | 1.05x | 368.1 | 353.3 | 1.04x |
| 15566 | backward | 625.6 | 582.9 | 1.07x | 623.8 | 581.6 | 1.07x |
| 15566 | checkpoint | 740.7 | 682.0 | 1.09x | 738.0 | 680.1 | 1.08x |
| 15590 | forward | 372.4 | 353.9 | 1.05x | 370.2 | 353.7 | 1.05x |
| 15590 | backward | 623.1 | 583.1 | 1.07x | 622.4 | 582.7 | 1.07x |
| 15590 | checkpoint | 740.7 | 682.3 | 1.09x | 737.9 | 680.8 | 1.08x |
| 16114 | forward | 380.9 | 364.9 | 1.04x | 381.1 | 364.8 | 1.04x |
| 16114 | backward | 638.9 | 598.2 | 1.07x | 638.1 | 597.2 | 1.07x |
| 16114 | checkpoint | 756.7 | 699.5 | 1.08x | 755.8 | 698.6 | 1.08x |
| 16132 | forward | 383.2 | 365.7 | 1.05x | 383.6 | 365.5 | 1.05x |
| 16132 | backward | 647.4 | 605.2 | 1.07x | 646.4 | 604.1 | 1.07x |
| 16132 | checkpoint | 767.3 | 706.9 | 1.09x | 765.5 | 705.3 | 1.09x |
| 16164 | forward | 382.2 | 366.3 | 1.04x | 382.8 | 365.9 | 1.05x |
| 16164 | backward | 647.9 | 604.8 | 1.07x | 646.7 | 603.6 | 1.07x |
| 16164 | checkpoint | 765.0 | 707.7 | 1.08x | 764.9 | 706.1 | 1.08x |
| 16263 | forward | 383.1 | 367.7 | 1.04x | 383.4 | 367.6 | 1.04x |
| 16263 | backward | 650.9 | 605.9 | 1.07x | 648.6 | 604.8 | 1.07x |
| 16263 | checkpoint | 767.6 | 707.2 | 1.09x | 766.0 | 705.8 | 1.09x |
| 32768 | forward | 745.8 | 726.0 | 1.03x | 747.0 | 725.7 | 1.03x |
| 32768 | backward | 1264.3 | 1191.9 | 1.06x | 1260.8 | 1189.1 | 1.06x |
| 32768 | checkpoint | 1481.2 | 1387.1 | 1.07x | 1479.3 | 1385.5 | 1.07x
|
| 65536 | forward | 1472.9 | 1431.7 | 1.03x | 1473.5 | 1431.7 | 1.03x |
| 65536 | backward | 2430.8 | 2317.8 | 1.05x | 2428.0 | 2316.4 | 1.05x |
| 65536 | checkpoint | 2853.6 | 2690.5 | 1.06x | 2850.9 | 2688.5 | 1.06x
|

**NVIDIA B200 (sm_100a), CUDA 13.4; kernel time per call in
microseconds, median of paired runs; two independent sessions (1 / 2);
speedup = previous / this PR**

| T (tokens) | Path | Previous (µs), session 1 | This PR (µs), session 1
| Speedup, session 1 | Previous (µs), session 2 | This PR (µs), session
2 | Speedup, session 2 |
|---:|---|---:|---:|---:|---:|---:|---:|
| 1024 | forward | 44.3 | 42.4 | 1.04x | 44.3 | 42.4 | 1.04x |
| 1024 | backward | 76.7 | 68.5 | 1.12x | 76.8 | 68.5 | 1.12x |
| 1024 | checkpoint | 97.5 | 87.4 | 1.11x | 97.4 | 87.2 | 1.12x |
| 4096 | forward | 111.1 | 109.1 | 1.02x | 111.0 | 109.1 | 1.02x |
| 4096 | backward | 215.1 | 190.5 | 1.13x | 214.7 | 190.1 | 1.13x |
| 4096 | checkpoint | 252.3 | 226.0 | 1.12x | 252.3 | 225.7 | 1.12x |
| 8192 | forward | 210.9 | 203.3 | 1.04x | 210.9 | 203.2 | 1.04x |
| 8192 | backward | 376.9 | 345.4 | 1.09x | 376.5 | 344.7 | 1.09x |
| 8192 | checkpoint | 448.0 | 409.1 | 1.10x | 447.5 | 408.6 | 1.10x |
| 14928 | forward | 369.7 | 357.7 | 1.03x | 366.6 | 356.8 | 1.03x |
| 14928 | backward | 636.5 | 594.6 | 1.07x | 634.8 | 592.6 | 1.07x |
| 14928 | checkpoint | 755.2 | 700.6 | 1.08x | 750.3 | 698.3 | 1.07x |
| 15288 | forward | 377.4 | 364.3 | 1.04x | 376.5 | 363.7 | 1.04x |
| 15288 | backward | 651.2 | 609.0 | 1.07x | 649.1 | 607.5 | 1.07x |
| 15288 | checkpoint | 771.6 | 715.9 | 1.08x | 769.2 | 714.4 | 1.08x |
| 15566 | forward | 381.5 | 368.2 | 1.04x | 380.7 | 367.8 | 1.04x |
| 15566 | backward | 667.1 | 623.4 | 1.07x | 664.9 | 621.4 | 1.07x |
| 15566 | checkpoint | 788.5 | 729.6 | 1.08x | 785.0 | 727.6 | 1.08x |
| 15590 | forward | 382.8 | 370.3 | 1.03x | 382.0 | 369.7 | 1.03x |
| 15590 | backward | 670.0 | 624.8 | 1.07x | 667.4 | 622.7 | 1.07x |
| 15590 | checkpoint | 791.2 | 733.5 | 1.08x | 788.6 | 731.2 | 1.08x |
| 16114 | forward | 391.4 | 378.5 | 1.03x | 391.3 | 378.1 | 1.03x |
| 16114 | backward | 678.4 | 633.9 | 1.07x | 675.4 | 632.1 | 1.07x |
| 16114 | checkpoint | 799.3 | 741.4 | 1.08x | 796.6 | 739.4 | 1.08x |
| 16132 | forward | 391.6 | 378.5 | 1.03x | 391.8 | 378.3 | 1.04x |
| 16132 | backward | 684.7 | 644.2 | 1.06x | 682.7 | 642.8 | 1.06x |
| 16132 | checkpoint | 806.7 | 751.4 | 1.07x | 804.4 | 749.7 | 1.07x |
| 16164 | forward | 392.7 | 379.8 | 1.03x | 392.3 | 379.3 | 1.03x |
| 16164 | backward | 684.9 | 644.7 | 1.06x | 683.5 | 643.8 | 1.06x |
| 16164 | checkpoint | 806.8 | 752.4 | 1.07x | 805.2 | 750.9 | 1.07x |
| 16263 | forward | 393.8 | 381.1 | 1.03x | 394.3 | 381.0 | 1.03x |
| 16263 | backward | 685.1 | 643.8 | 1.06x | 682.9 | 641.7 | 1.06x |
| 16263 | checkpoint | 807.1 | 751.9 | 1.07x | 805.2 | 749.3 | 1.07x |
| 32768 | forward | 768.2 | 744.2 | 1.03x | 768.3 | 743.6 | 1.03x |
| 32768 | backward | 1333.9 | 1264.4 | 1.05x | 1328.3 | 1258.8 | 1.06x |
| 32768 | checkpoint | 1563.2 | 1463.0 | 1.07x | 1558.6 | 1456.2 | 1.07x
|
| 65536 | forward | 1518.9 | 1470.7 | 1.03x | 1519.0 | 1468.6 | 1.03x |
| 65536 | backward | 2673.2 | 2551.6 | 1.05x | 2654.4 | 2509.3 | 1.06x |
| 65536 | checkpoint | 3077.3 | 2842.3 | 1.08x | 3127.5 | 2923.1 | 1.07x
|

**NVIDIA R200 (sm_107a), CUDA 13.4; kernel time per call in
microseconds, median of paired runs; two independent sessions (1 / 2);
speedup = previous / this PR**

| T (tokens) | Path | Previous (µs), session 1 | This PR (µs), session 1
| Speedup, session 1 | Previous (µs), session 2 | This PR (µs), session
2 | Speedup, session 2 |
|---:|---|---:|---:|---:|---:|---:|---:|
| 1024 | forward | 36.5 | 33.1 | 1.10x | 36.1 | 32.4 | 1.11x |
| 1024 | backward | 57.8 | 51.3 | 1.13x | 57.8 | 51.4 | 1.12x |
| 1024 | checkpoint | 74.4 | 66.2 | 1.12x | 74.4 | 66.3 | 1.12x |
| 4096 | forward | 90.7 | 80.1 | 1.13x | 90.1 | 78.8 | 1.14x |
| 4096 | backward | 143.4 | 133.1 | 1.08x | 143.6 | 133.2 | 1.08x |
| 4096 | checkpoint | 173.6 | 161.2 | 1.08x | 173.8 | 161.2 | 1.08x |
| 8192 | forward | 164.4 | 141.8 | 1.16x | 161.6 | 137.9 | 1.17x |
| 8192 | backward | 247.3 | 235.4 | 1.05x | 247.5 | 235.5 | 1.05x |
| 8192 | checkpoint | 297.3 | 280.7 | 1.06x | 297.9 | 281.3 | 1.06x |
| 14928 | forward | 283.7 | 243.8 | 1.16x | 278.4 | 237.8 | 1.17x |
| 14928 | backward | 421.4 | 408.4 | 1.03x | 421.9 | 408.7 | 1.03x |
| 14928 | checkpoint | 502.0 | 479.5 | 1.05x | 504.0 | 479.9 | 1.05x |
| 15288 | forward | 288.8 | 252.4 | 1.14x | 283.4 | 245.6 | 1.15x |
| 15288 | backward | 431.8 | 418.7 | 1.03x | 433.8 | 419.8 | 1.03x |
| 15288 | checkpoint | 513.3 | 493.8 | 1.04x | 515.8 | 495.5 | 1.04x |
| 15566 | forward | 293.5 | 256.4 | 1.14x | 286.9 | 248.8 | 1.15x |
| 15566 | backward | 435.9 | 423.4 | 1.03x | 436.1 | 423.7 | 1.03x |
| 15566 | checkpoint | 517.2 | 500.3 | 1.03x | 518.9 | 500.2 | 1.04x |
| 15590 | forward | 292.8 | 256.2 | 1.14x | 287.1 | 249.1 | 1.15x |
| 15590 | backward | 438.7 | 427.0 | 1.03x | 440.8 | 427.9 | 1.03x |
| 15590 | checkpoint | 520.5 | 503.2 | 1.03x | 522.7 | 504.2 | 1.04x |
| 16114 | forward | 301.3 | 263.3 | 1.14x | 294.9 | 255.4 | 1.16x |
| 16114 | backward | 452.4 | 438.8 | 1.03x | 455.1 | 439.8 | 1.03x |
| 16114 | checkpoint | 533.7 | 516.7 | 1.03x | 535.7 | 516.8 | 1.04x |
| 16132 | forward | 301.1 | 263.2 | 1.14x | 295.4 | 255.9 | 1.15x |
| 16132 | backward | 452.6 | 438.3 | 1.03x | 453.8 | 437.9 | 1.04x |
| 16132 | checkpoint | 535.3 | 515.9 | 1.04x | 536.5 | 515.0 | 1.04x |
| 16164 | forward | 302.0 | 263.2 | 1.15x | 295.6 | 255.8 | 1.16x |
| 16164 | backward | 454.4 | 438.5 | 1.04x | 456.8 | 440.3 | 1.04x |
| 16164 | checkpoint | 537.6 | 515.5 | 1.04x | 538.9 | 517.4 | 1.04x |
| 16263 | forward | 303.0 | 264.8 | 1.14x | 296.9 | 257.7 | 1.15x |
| 16263 | backward | 457.0 | 443.3 | 1.03x | 458.6 | 443.8 | 1.03x |
| 16263 | checkpoint | 541.0 | 520.9 | 1.04x | 542.3 | 521.4 | 1.04x |
| 32768 | forward | 586.3 | 509.0 | 1.15x | 573.7 | 494.5 | 1.16x |
| 32768 | backward | 878.8 | 860.0 | 1.02x | 881.0 | 861.3 | 1.02x |
| 32768 | checkpoint | 1029.7 | 994.6 | 1.04x | 1032.8 | 996.5 | 1.04x |
| 65536 | forward | 1149.6 | 997.6 | 1.15x | 1126.4 | 967.4 | 1.16x |
| 65536 | backward | 1708.9 | 1669.6 | 1.02x | 1708.0 | 1671.3 | 1.02x |
| 65536 | checkpoint | 1993.0 | 1934.2 | 1.03x | 1995.0 | 1935.0 | 1.03x
|

Cake has no other mHC training variant (no other data type, layout or
fused form), and these kernels ship on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added architecture-specific GPU optimizations for Cake mHC training,
covering forward and backward computations.
  * Improved device-aware selection of optimized kernels.

* **Compatibility**
* Expanded support for additional GPU architecture and kernel variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [94b5e26](https://github.com/flashinfer-ai/flashinfer/commit/94b5e266a966146b5da8cba4e70f9cea6260de5f)

- **作者**: Yang Xu
- **时间**: 2026-10-24T23:36:59Z
- **提交信息**: perf(moe): add grouped BF16 TC decode on Hopper and SM120 (#7194)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add grouped BF16 Tensor Core candidates to `frost_low_latency` on Hopper
SM90 and SM120. At four/eight decode tokens, several routes often select
the same expert; loading its weights once for a small group can
outperform evaluating each route independently.

Each CTA discovers matching expert IDs from the current inputs. Both
paths read the existing prepared up/gate layout using TMA, perform FC1
plus activation and FC2, and use an ascending-slot FP32 combine. Hopper
uses WGMMA; SM120 uses warp MMA. They share route grouping, activation,
typed intermediate/output semantics, and the pointer/stream-safe cached
launch wrapper. The device pipelines are adapted from the NVIDIA CUTLASS
CuTe DSL GEMM examples, with their license notices retained.

Admission is intentionally bounded: BF16 input/weights/output, default
SwiGLU, H=2048, I=512, top-k=10, T=4 or 8, finalized output. Hopper adds
three configurations; SM120 adds two at T4 and four at T8. The original
16 FMA candidates and the untuned FMA default remain. Other shapes,
activations and formats keep their current advertised tactics. There is
no public signature/default change.

**Measured complete routed-expert GPU intervals**, same checkpoint,
shape, route pattern and cache condition. H2048/I512/E512/K10, BF16
SwiGLU, all tokens select the same ten experts with shuffled slots. H100
rows use current fix `a806b9007` and seed7203; explicitly marked SM120
rows are from before the score fix (seed7191), pending their post-fix
timing rerun:

| GPU / tokens | Comparator | Warm baseline → grouped TC (µs) | Speedup
| Cold baseline → grouped TC (µs) | Speedup |
|---|---|---:|---:|---:|---:|
| H100 80GB HBM3 / T4 | existing Frost FMA | 46.479 → 36.472 | 1.274× |
54.792 → 43.663 | 1.255× |
| H100 80GB HBM3 / T8 | CUTLASS | 48.328 → 45.184 | 1.070× | 59.464 →
52.279 | 1.137× |
| RTX PRO 6000 Blackwell Workstation / T4 (pre-fix) | cuTile warm;
existing Frost FMA cold | 29.736 → 20.088 | 1.48× | 54.312 → 49.888 |
1.09× |
| RTX PRO 6000 Blackwell Workstation / T8 (pre-fix) | cuTile warm;
CUTLASS cold | 32.840 → 23.888 | 1.37× | 64.176 → 64.720 | 0.99× |

Each cell uses a paired run; different cells are not combined into a
ratio. We select candidates, freeze the winners, then measure ABBA CUPTI
CUDA Graph intervals. Existing backends use their runner's compound
candidate generator plus heuristic, not an exhaustive Cartesian search.
The listed comparator is the faster measured applicable family for that
case/cache state; cuDNN grouped and the other native paths were also
audited. Two additional SM120 route seeds retained T4 warm gains of
~1.36× and T8 gains of ~1.34–1.40× against cuTile; a second Hopper seed
retained T4/T8 gains.

**Boundaries:** disjoint routes favor FMA; partially shared SM120 routes
can favor FMA depending on expert addresses; SM120 T8/shared/cold is
approximately parity. These are tuning candidates, not a
token-count-only dispatch rule. Measurements exclude host enqueue,
preparation, router-network evaluation, shared experts, EP communication
and serving/model throughput.

Reproducer (CuTe DSL 4.8.0, tvm-ffi 0.1.14.post1, CUPTI Python support):
```bash
PYTHONPATH=. python benchmarks/bench_frost_low_latency_grouped_tc.py --tokens 4 --route-seed 7191 --baseline cutlass_bf16 --output grouped-t4.json
# Repeat --tokens 8, --route-seed 7192/7193, and --baseline cutile_bf16.
# Also audit --baseline cudnn_grouped_gemm_bf16 when supported.
```
The JSON records source hashes, software/GPU, candidates, frozen
choices, raw samples and reference errors. H100 used PyTorch
2.14.0a0+nv26.09 / CUDA 13.4; SM120 used PyTorch 2.14.1+cu130 / CUDA
13.0. Each run verifies its actual import/source path.

For the unified API, enable the existing
`FrostLowLatencyConfig(max_num_tokens=8)` option and profile
representative routes with the normal autotuner. The default maximum
remains two tokens; Frost remains explicit opt-in.

The reproducer requires working CUPTI >= 13 and records its version. It
fails before timing if the dependency is absent, preventing CUDA-event
fallback from being mislabeled as a cold-cache measurement. Existing
H100/SM120 qualification used CUPTI. Three dependency-guard checks
passed (absent, old, supported).

## 🔍 Related Issues

Continues the Frost low-latency expansion from #6626. The SM120 NVFP4 TC
path in #7190 is a separate pipeline; this PR adds BF16-weight grouped
projection candidates.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run `pre-commit run --files <all changed files>` and fixed
reported issues (scoped to this batch).

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted tests pass on both supported architectures.

Latest head `a806b9007`: **175 passed, 1 expected skip on each H100 and
SM120**. The new invalid-route NaN/Inf regression fails on the old
native kernel and all12 cases pass on both GPUs after the fix. Cases
cover packed/unpacked, T4/T8, negative/out-of-range IDs and score
mutation after CUDA Graph capture. The full SM120 suite finished before
its lease boundary; only the subsequent performance rerun was
interrupted.

CI's older CuTe DSL skips the new TC cases; a green CI job is not
counted as target-GPU execution evidence. The source-verified native
CuTe DSL4.8 runs above and the independent H100 review are separate
evidence.

Earlier qualification on **each** of H100 and SM120:
- Shared-runtime suite plus existing BF16 tests: **139 passed, 1
skipped** (the skip is an existing SM10x-only case).
- Strengthened new suite with independent weight/input/output pointers
and streams: **90 passed**.
- Compute Sanitizer: **12 cases each** under memcheck, racecheck and
synccheck; zero errors/hazards.
- After the final compile-time launch typing fix: **18 targeted
graph-binding/admitted-tactic tests passed**, and the T4 paired
benchmark was repeated on the verified final source.

The tests cover BF16/FP16/mixed output, supported activation lowerings,
repeated/invalid/changing routes, partial groups, poisoned buffers,
retained CUDA Graph replay, independent weights and concurrent streams.
Broader device correctness does not broaden the bounded advertised
performance admission. The benchmark validates every timed candidate and
the actual graph destination against an independent
FP64-dot/typed-boundary reference; tolerances were not relaxed.

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

The combine skips invalid live route IDs before loading/multiplying
their score, matching the retained FMA path even when padding scores are
non-finite. The compiled-entry version changed for this fix. Normal
auto-merge remains off until the new head receives review; required
checks remain enforced.

The reproducer requires working CUPTI >= 13, records its version, and
fails before timing if absent. Existing H100/SM120 qualification used
CUPTI; three guard checks passed.


Please focus on stage lifetime, the original up/gate shared-memory
layout slices, and live route ownership. SM120 requires CTA
synchronization both before ldmatrix and before releasing/reusing the
stage. Hopper waits for WGMMA completion before stage reuse.

Compiled entries retain immutable metadata only; all eight tensors and
the current stream are bound per call. The BF16 tuning policy ID changes
to invalidate stale candidate sets. A profiling winner can cease to be
fastest when routing/cache behavior changes, so the existing FMA
candidates remain essential.

The first SM120 test attempt incorrectly skipped the new cases due to a
test guard; that guard was fixed and the actual runs above replaced that
evidence. The final mypy check also caught incompatible constexpr-branch
local types; architecture-specific launch locals fix it without changing
the device kernels. A100 and larger-shape/other-activation experiments
are follow-ups, outside this diff.

### [5e45550](https://github.com/flashinfer-ai/flashinfer/commit/5e4555094c329cee6d035791eec1f73e96980f59)

- **作者**: Yang Xu
- **时间**: 2026-10-24T22:39:24Z
- **提交信息**: fix(moe): reserve W4A16 scratch for direct routes before graph capture (#7195)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix CUDA Graph capture for SM120 W4A16 direct routing when several
routes share a small expert bank. For example, BF16
T8/H2048/I512/E16/top-k10 can warm up successfully and then fail capture
with `W4A16 GEMM scratch is not initialized for CUDA graph capture`.

Both workspace planners sized GEMM scratch from packed-route capacity.
Direct routing instead reserves a full block for every route, so packed
capacity can underestimate the required scratch when routes repeat an
expert. Eager execution masks the defect by allocating a temporary;
capture cannot do that.

Size scratch for the maximum of packed capacity and the bounded
direct-routing region in both `plan_w4a16_buffers` and
`_w4a16_workspace_geometry`. Keep route-pack buffers/block counts
unchanged, and share the existing eight-token direct-routing upper bound
with kernel eligibility. The per-SM scratch cap still applies. No kernel
math, routing eligibility, or API signature changes.

The regression expands the existing BF16/FP16 live-graph tests to
E16/H2048/I512/K10, tests both public workspace factories for BF16, and
checks both planners across small/large token and expert counts.

## 🔍 Related Issues

Found while following up on #7190; also covers the FP16 direct-routing
path introduced by #7186. This is independent of the grouped BF16
kernels in #7194.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run `pre-commit run --files <changed files>` and fixed
reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] The targeted suite passes on SM120.

**RED:** the T8/H2048/I512/E16/K10 graph test fails on the original
implementation for each workspace factory with the scratch-capacity
exception. Both original failures are preserved.

**GREEN:** **130 passed** on RTX PRO 6000 Blackwell Workstation (SM120),
CuTe DSL4.8.0, PyTorch2.14.1+cu130, tvm-ffi0.1.14.post1:
```bash
pytest -q -rs tests/moe/test_b12x_w4a16_scratch.py tests/moe/test_b12x_w4a16_bf16_tc_decode.py tests/moe/test_b12x_w4a16_fp16_direct.py tests/moe/test_b12x_w4a16_route_pack.py
```
The graph tests retain independent numerical references, changed
routes/inputs/scores, negative routes and poisoned outputs. Tolerances
are unchanged. Targeted mypy/ruff/pre-commit checks pass.

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

Scratch memory may increase for small expert banks that were previously
under-allocated. Only the direct-routing token envelope contributes to
that extra bound; packed routing capacities themselves are unchanged.
The shared maximum must stay consistent with any future expansion of
direct routing.

This fixes allocation/capture correctness. It does not change the BF16
atomic-combine repeatability semantics; fixed-order fallback selection
is a separate follow-up.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded W4A16 routing capacity for selected workloads, including
configurations with more experts and larger top-k values.
* Updated workspace sizing to accommodate the expanded routing capacity
while keeping packed route buffers unchanged.
* **Tests**
* Added coverage across additional model dimensions, token counts,
expert counts, and workspace allocation modes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [54459f0](https://github.com/flashinfer-ai/flashinfer/commit/54459f0872e539a71c32e557e40f77a3790c8907)

- **作者**: eigen
- **时间**: 2026-10-24T22:22:09Z
- **提交信息**: perf(cake_dsa_indexer): 16384-slot candidate buffer floor and an early next-tile probe in the wide scan programs (#7187)

This PR speeds up the Cake DSA indexer top-k scan behind
`flashinfer.dsa_indexer.dsa_indexer_topk`, which has only one data-type
variant (BF16 queries and keys, FP32 head weights and scores). On
sm_100a and sm_103a, the host plan raises the per-query candidate-buffer
floor from 8192 to 16384 slots, so short and medium units compact less
often. The selection-trigger check period follows the new capacity. The
trade is a larger persistent workspace for `top_k <= 2048` calls on
those units: 57 MiB to 114 MiB for narrow and l6 units, and 76 MiB to
152 MiB for wide units on a 152-SM part. Calls that already used 16384
or more slots are unchanged. The previous plan is kept whenever
`sample_tiles_max=0` turns off the sampled first threshold. Two wide
scan programs now probe the next tile's completion right after releasing
the current accumulator stage, instead of at the end of the tile.
Against the previous Cake version of this kernel, the speedup on GB200
is 1.12x on Z2cp, 1.10x on Z3cp and 1.03x on Z2 and Z3. On GB300 it is
1.16x on Z3cp, 1.07x on Z3, 1.06x on Z2cp, 1.04x on P1sink and 1.03x on
S4sink. All other rows are 0.98x–1.02x, and output is bit-identical on
every shape.

Speedup on GB200:

GB200 (NVIDIA GB200, sm_100a, CUDA 13.4); ms = median of the two
arm-order processes of the CUPTI kernel time; speedup = previous / this
PR.

| row | shape | T (queries) | Tkv (keys) | segments | top-k | previous
Cake kernel ms | this PR ms | speedup |
|---|---|---|---|---|---|---|---|---|
| Z1 | #7042 repro: 262k document, CP16 zigzag rank 0 | 16384 | 270336 |
2 | 2048 | 13.169 | 13.122 | 1.00x |
| Z1k4096 | Z1 with top-k 4096 | 16384 | 270336 | 2 | 4096 | 14.056 |
14.017 | 1.00x |
| Z1k256 | Z1 with top-k 256 | 16384 | 270336 | 2 | 256 | 12.908 |
12.777 | 1.01x |
| Z2 | 8 x 32k documents, full causal | 262144 | 262144 | 8 | 2048 |
33.835 | 32.862 | 1.03x |
| Z2cp | 8 x 32k documents, CP16 zigzag rank 0 | 16384 | 270336 | 16 |
2048 | 2.236 | 1.991 | 1.12x |
| Z3 | packed 4k-64k documents, full causal | 169984 | 169984 | 8 | 2048
| 24.994 | 24.217 | 1.03x |
| Z3cp | packed 4k-64k documents, CP16 zigzag rank 0 | 10624 | 175296 |
16 | 2048 | 1.687 | 1.538 | 1.10x |
| P1sink | recorded P1 geometry with sink statistics | 16231 | 268757 |
8 | 2048 | 3.425 | 3.371 | 1.02x |
| S4sink | one 64k causal document, sink statistics | 65536 | 65536 | 1
| 2048 | 14.792 | 14.599 | 1.01x |
| S6sink | one 262k causal document, sink statistics | 262144 | 262144 |
1 | 2048 | 213.874 | 214.129 | 1.00x |
| P1 | recorded packed call | 16231 | 268757 | 8 | 2048 | 3.541 | 3.499
| 1.01x |
| P1_peaked | P1 with dominating keys | 16231 | 268757 | 8 | 2048 |
3.582 | 3.583 | 1.00x |
| P2 | second recorded token count, boundaries derived | 16172 | 267520
| 8 | 2048 | 3.569 | 3.537 | 1.01x |
| P3 | P1 with top-k 4096 | 16231 | 268757 | 8 | 4096 | 3.859 | 3.873 |
1.00x |
| S1 | single causal document N = 8192 | 8192 | 8192 | 1 | 2048 | 0.429
| 0.428 | 1.00x |
| S2 | single causal document N = 16384 | 16384 | 16384 | 1 | 2048 |
1.240 | 1.234 | 1.00x |
| S3 | single causal document N = 32768 | 32768 | 32768 | 1 | 2048 |
3.997 | 3.948 | 1.01x |
| S4 | single causal document N = 65536 | 65536 | 65536 | 1 | 2048 |
14.847 | 14.724 | 1.01x |
| S5 | single causal document N = 131072 | 131072 | 131072 | 1 | 2048 |
56.343 | 56.357 | 1.00x |
| S6 | single causal document N = 262144 | 262144 | 262144 | 1 | 2048 |
217.062 | 216.948 | 1.00x |
| S7 | single causal document N = 524288 | 524288 | 524288 | 1 | 2048 |
883.592 | 884.222 | 1.00x |
| S4_peaked | S4 with dominating keys | 65536 | 65536 | 1 | 2048 |
14.870 | 14.725 | 1.01x |
| C1 | CP tail 4096 x 65536 | 4096 | 65536 | 1 | 2048 | 1.741 | 1.735 |
1.00x |
| C2 | CP tail 4096 x 131072 | 4096 | 131072 | 1 | 2048 | 3.273 | 3.325
| 0.98x |
| C3 | packed 8 x (2048 x 32768) | 16384 | 262144 | 8 | 2048 | 3.418 |
3.485 | 0.98x |
| V1 | N = 65536, ratio 2 | 65536 | 32768 | 1 | 2048 | 8.124 | 8.097 |
1.00x |
| V2 | N = 65536, top-k 256 | 65536 | 65536 | 1 | 256 | 13.809 | 13.687
| 1.01x |
| V3 | N = 65536, top-k 4096 | 65536 | 65536 | 1 | 4096 | 15.974 |
16.001 | 1.00x |
| S8 | single causal document N = 1048576 | 1048576 | 1048576 | 1 | 2048
| 3910.764 | 3911.341 | 1.00x |

Speedup on GB300:

GB300 (NVIDIA GB300, sm_103a, CUDA 13.4); ms = median of the two
arm-order processes of the CUPTI kernel time; speedup = previous / this
PR. Rows Z1, Z1k4096, Z1k256, S6sink, S5, S6, S7, S8, C1, C2 and V2 are
from the earlier record (identical dispatch plan); the other 18 rows
were re-measured on the final head.

| row | shape | T (queries) | Tkv (keys) | segments | top-k | previous
Cake kernel ms | this PR ms | speedup |
|---|---|---|---|---|---|---|---|---|
| Z1 | #7042 repro: 262k document, CP16 zigzag rank 0 | 16384 | 270336 |
2 | 2048 | 12.023 | 12.025 | 1.00x |
| Z1k4096 | Z1 with top-k 4096 | 16384 | 270336 | 2 | 4096 | 15.297 |
15.288 | 1.00x |
| Z1k256 | Z1 with top-k 256 | 16384 | 270336 | 2 | 256 | 11.445 |
11.424 | 1.00x |
| Z2 | 8 x 32k documents, full causal | 262144 | 262144 | 8 | 2048 |
31.416 | 30.854 | 1.02x |
| Z2cp | 8 x 32k documents, CP16 zigzag rank 0 | 16384 | 270336 | 16 |
2048 | 2.011 | 1.890 | 1.06x |
| Z3 | packed 4k-64k documents, full causal | 169984 | 169984 | 8 | 2048
| 24.331 | 22.837 | 1.07x |
| Z3cp | packed 4k-64k documents, CP16 zigzag rank 0 | 10624 | 175296 |
16 | 2048 | 1.757 | 1.518 | 1.16x |
| P1sink | recorded P1 geometry with sink statistics | 16231 | 268757 |
8 | 2048 | 3.687 | 3.549 | 1.04x |
| S4sink | one 64k causal document, sink statistics | 65536 | 65536 | 1
| 2048 | 14.848 | 14.457 | 1.03x |
| S6sink | one 262k causal document, sink statistics | 262144 | 262144 |
1 | 2048 | 194.627 | 194.555 | 1.00x |
| P1 | recorded packed call | 16231 | 268757 | 8 | 2048 | 3.395 | 3.381
| 1.00x |
| P1_peaked | P1 with dominating keys | 16231 | 268757 | 8 | 2048 |
3.403 | 3.381 | 1.01x |
| P2 | second recorded token count, boundaries derived | 16172 | 267520
| 8 | 2048 | 3.395 | 3.376 | 1.01x |
| P3 | P1 with top-k 4096 | 16231 | 268757 | 8 | 4096 | 3.671 | 3.670 |
1.00x |
| S1 | single causal document N = 8192 | 8192 | 8192 | 1 | 2048 | 0.412
| 0.410 | 1.00x |
| S2 | single causal document N = 16384 | 16384 | 16384 | 1 | 2048 |
1.195 | 1.193 | 1.00x |
| S3 | single causal document N = 32768 | 32768 | 32768 | 1 | 2048 |
3.748 | 3.732 | 1.00x |
| S4 | single causal document N = 65536 | 65536 | 65536 | 1 | 2048 |
13.521 | 13.377 | 1.01x |
| S5 | single causal document N = 131072 | 131072 | 131072 | 1 | 2048 |
48.906 | 48.944 | 1.00x |
| S6 | single causal document N = 262144 | 262144 | 262144 | 1 | 2048 |
186.841 | 186.950 | 1.00x |
| S7 | single causal document N = 524288 | 524288 | 524288 | 1 | 2048 |
772.321 | 771.830 | 1.00x |
| S4_peaked | S4 with dominating keys | 65536 | 65536 | 1 | 2048 |
13.399 | 13.324 | 1.01x |
| C1 | CP tail 4096 x 65536 | 4096 | 65536 | 1 | 2048 | 1.555 | 1.555 |
1.00x |
| C2 | CP tail 4096 x 131072 | 4096 | 131072 | 1 | 2048 | 2.939 | 2.935
| 1.00x |
| C3 | packed 8 x (2048 x 32768) | 16384 | 262144 | 8 | 2048 | 3.195 |
3.195 | 1.00x |
| V1 | N = 65536, ratio 2 | 65536 | 32768 | 1 | 2048 | 7.502 | 7.497 |
1.00x |
| V2 | N = 65536, top-k 256 | 65536 | 65536 | 1 | 256 | 12.448 | 12.412
| 1.00x |
| V3 | N = 65536, top-k 4096 | 65536 | 65536 | 1 | 4096 | 14.509 |
14.536 | 1.00x |
| S8 | single causal document N = 1048576 | 1048576 | 1048576 | 1 | 2048
| 3319.891 | 3320.218 | 1.00x |

Cake ships no other variant of this kernel; the next-tile probe is on
only in the sm_100a sampled wide program and the sm_103a no-sample-fit
wide program, and the family ships on sm_100a (GB200), sm_103a (GB300)
and sm_107a (R200), where the kernel and its plan are unchanged in this
PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Candidate buffer capacity is now configured separately when sampling
is disabled, allowing unsampled workloads to use their own capacity
settings.
* **Bug Fixes**
* Updated GPU execution sequencing for specific hardware configurations.
* **Documentation**
* Clarified how disabling sampling affects candidate capacity and
workspace requirements. The documented workspace examples now use a
16,384-slot capacity floor and state that disabling sampling does not
require additional workspace.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [b1204ee](https://github.com/flashinfer-ai/flashinfer/commit/b1204ee8972d413c934da776d58342e466d09534)

- **作者**: eigen
- **时间**: 2026-10-24T22:21:53Z
- **提交信息**: feat(cake_vsa_sm90): batch 8 V^T chunks in the FP8 grouped-query shared-transposer queue program (#7185)

FlashInfer's Cake backend for variable block-sparse attention on Hopper
(`VariableBlockSparseAttentionWrapper(backend="cake")`, sm_90a) ships
two data types, BF16 and Sage-FP8 (E4M3 inputs with per-head scales,
BF16 output). Each has multi-head programs and grouped-query programs
(num_qo_heads = g × num_kv_heads, g ∈ {2, 4, 8}); #7167 added the
grouped-query programs. This PR updates one of them in place: the
Sage-FP8 grouped-query shared-transposer queue program, which is the
persistent queue program that serves the long grouped-query FP8 rows.
Each shared-transposer hand-off now carries eight V^T chunks instead of
two. The baseline is the previous Cake version of this program, shipped
by #7167, with two V^T chunks per hand-off. Against that baseline the
new program is faster on all 27 shapes below, with a geometric mean of
1.0077× (range 1.0035–1.0120×). A second process using the same protocol
was also faster on all 27 shapes (geometric mean 1.008×, range
1.0035–1.0125×).

Kernel-only time on NVIDIA H100 80GB HBM3 (Hopper, sm_90a), CUDA 13.4
toolkit (JIT-compiled; torch 2.14.1+cu130), driver 535.216.03, using
paired same-process CUPTI timing of the previous and new program on the
same inputs with cold L2, 3 groups × 128 samples and both interleaving
orders. The table shows one process. Shapes are named
h<num_qo_heads>-m<query tokens>-n<key/value tokens>-k<KV blocks per
query block>-ragged<0|1>-scale0-g<group size>, and dtype e4m3 means
Sage-FP8.

| shape | dtype | previous µs | this µs | speedup |
|---|---|---|---|---|
| h12-m109632-n109632-k32-ragged0-scale0-g4 | e4m3 | 2021.178 | 2008.233
| 1.006x |
| h12-m109632-n109632-k64-ragged0-scale0-g4 | e4m3 | 3880.227 | 3848.387
| 1.008x |
| h12-m109632-n109632-k64-ragged1-scale0-g4 | e4m3 | 2011.978 | 1999.737
| 1.006x |
| h12-m32768-n32768-k32-ragged0-scale0-g4 | e4m3 | 597.694 | 591.950 |
1.010x |
| h12-m32768-n32768-k64-ragged0-scale0-g4 | e4m3 | 1139.485 | 1125.932 |
1.012x |
| h12-m32768-n32768-k64-ragged1-scale0-g4 | e4m3 | 593.374 | 589.694 |
1.006x |
| h12-m75648-n75648-k32-ragged0-scale0-g4 | e4m3 | 1367.323 | 1357.628 |
1.007x |
| h12-m75648-n75648-k64-ragged0-scale0-g4 | e4m3 | 2620.024 | 2598.343 |
1.008x |
| h12-m75648-n75648-k64-ragged1-scale0-g4 | e4m3 | 1375.931 | 1367.819 |
1.006x |
| h32-m8192-n8192-k24-ragged0-scale0-g4 | e4m3 | 309.391 | 308.079 |
1.004x |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | e4m3 | 308.847 | 307.775 |
1.003x |
| h8-m109632-n109632-k32-ragged0-scale0-g4 | e4m3 | 1341.228 | 1330.700
| 1.008x |
| h8-m109632-n109632-k32-ragged0-scale0-g8 | e4m3 | 1328.316 | 1318.891
| 1.007x |
| h8-m109632-n109632-k64-ragged0-scale0-g4 | e4m3 | 2579.701 | 2555.637
| 1.009x |
| h8-m109632-n109632-k64-ragged0-scale0-g8 | e4m3 | 2551.655 | 2527.511
| 1.010x |
| h8-m109632-n109632-k64-ragged1-scale0-g4 | e4m3 | 1325.212 | 1317.356
| 1.006x |
| h8-m109632-n109632-k64-ragged1-scale0-g8 | e4m3 | 1299.900 | 1291.724
| 1.006x |
| h8-m32768-n32768-k32-ragged0-scale0-g4 | e4m3 | 401.918 | 398.207 |
1.009x |
| h8-m32768-n32768-k32-ragged0-scale0-g8 | e4m3 | 401.567 | 398.127 |
1.009x |
| h8-m32768-n32768-k64-ragged0-scale0-g4 | e4m3 | 764.174 | 755.726 |
1.011x |
| h8-m32768-n32768-k64-ragged0-scale0-g8 | e4m3 | 765.198 | 756.574 |
1.011x |
| h8-m75648-n75648-k32-ragged0-scale0-g4 | e4m3 | 900.029 | 894.014 |
1.007x |
| h8-m75648-n75648-k32-ragged0-scale0-g8 | e4m3 | 902.430 | 895.918 |
1.007x |
| h8-m75648-n75648-k64-ragged0-scale0-g4 | e4m3 | 1740.394 | 1726.315 |
1.008x |
| h8-m75648-n75648-k64-ragged0-scale0-g8 | e4m3 | 1739.642 | 1723.419 |
1.009x |
| h8-m75648-n75648-k64-ragged1-scale0-g4 | e4m3 | 898.446 | 892.942 |
1.006x |
| h8-m75648-n75648-k64-ragged1-scale0-g8 | e4m3 | 894.286 | 888.750 |
1.006x |

The other Cake variants of this kernel are the BF16 and Sage-FP8
multi-head programs and the BF16 grouped-query programs, all shipped by
earlier PRs of this backend; the family runs only on sm_90a (Hopper),
and other architectures have their own Cake block-sparse attention
backends.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Descriptor calculations now detect 64-bit integer overflow and invalid
division or modulo operations, returning clearer errors instead of
risking incorrect results.
  * Tensor-map descriptor dimensions and constraints remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [177eb53](https://github.com/flashinfer-ai/flashinfer/commit/177eb53ec6ca3be7d60165fe1a2406adc631608d)

- **作者**: eigen
- **时间**: 2026-10-24T22:21:20Z
- **提交信息**: perf(cake_nvfp4_svdquant): L2-promoted 64-row program for M 129 K 3072 on sm_103a (#7183)

`flashinfer.mm_nvfp4_svdquant(..., backend="cake")` computes the NVFP4
SVDQuant GEMM `out = BF16(alpha * (deq(A) @ deq(B)^T + D @ L1^T) +
bias)`. In this kernel, A and B are NVFP4 (E2M1) with E4M3 block scales.
The low-rank D / L1, the bias and the output are BF16, and accumulation
is FP32. Its Cake backend has one data-type / layout variant, with two
fused forms (with and without the fused bias), across LoRA ranks 32 / 64
/ 96 / 128. That variant ships for sm_100a and sm_103a as the vendorable
package `flashinfer/cake_nvfp4_svdquant_gemm_backend`. This PR is a
further tuning round of the same variant. On sm_103a (GB300), six of the
28 shapes below now dispatch to new builds of the 64-row program that
already served them. These shapes are (M, N, K, rank, bias) = (129,
3072, 3072, 32, 1), (129, 3072, 3072, 32, 0), (129, 3072, 3072, 64, 1),
(129, 3072, 3072, 96, 1), (129, 3072, 3072, 128, 1) and (129, 3072,
3072, 128, 0). In the new builds, the weight-stream TMA loads carry
256-byte L2 promotion: the weight tiles and their block scales are
promoted to 256-byte L2 lines, and only the TMA descriptor encodings
change. In the order listed, the six shapes speed up by 1.012, 1.011,
1.010, 1.010, 1.010 and 1.012 on GB300. Every other shape on GB300 keeps
its previous kernel build, and so does every shape on GB200 (sm_100a).
The GB300 rows for those shapes, and every GB200 row, are marked ‡
below. "Previous Cake" is the previous Cake release of this kernel,
measured in the same session as this PR's package.

**Speedup of the L2-promoted 64-row program over the previous Cake
kernel on NVIDIA GB300 (sm_103a), CUDA 13.4, median kernel time (CUPTI,
cold L2), session s1**

| M | N | K | rank | bias | previous Cake (µs) | this PR (µs) | speedup
vs previous Cake |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 129 | 3072 | 3072 | 32 | 1 | 5.73 | 5.66 | 1.012 |
| 129 | 3072 | 3072 | 32 | 0 | 5.66 | 5.60 | 1.011 |
| 129 | 3072 | 3072 | 64 | 1 | 5.79 | 5.73 | 1.010 |
| 129 | 3072 | 3072 | 96 | 1 | 5.82 | 5.76 | 1.010 |
| 129 | 3072 | 3072 | 128 | 1 | 5.92 | 5.86 | 1.010 |
| 129 | 3072 | 3072 | 128 | 0 | 5.86 | 5.79 | 1.012 |
| 129 | 3072 | 12288 | 32 | 0 | 10.66 | 10.66 | 1.000 ‡ |
| 129 | 3072 | 12288 | 32 | 1 | 10.69 | 10.69 | 1.000 ‡ |
| 129 | 3072 | 12288 | 128 | 0 | 10.78 | 10.78 | 1.000 ‡ |
| 129 | 3072 | 12288 | 128 | 1 | 10.78 | 10.78 | 1.000 ‡ |
| 6912 | 3072 | 3072 | 32 | 1 | 26.02 | 26.13 | 0.996 ‡ |
| 6912 | 3072 | 3072 | 64 | 1 | 26.30 | 26.34 | 0.998 ‡ |
| 6912 | 3072 | 3072 | 96 | 1 | 27.97 | 27.84 | 1.005 ‡ |
| 6912 | 3072 | 3072 | 128 | 1 | 28.29 | 28.37 | 0.997 ‡ |
| 6912 | 3072 | 12288 | 32 | 1 | 74.96 | 75.02 | 0.999 ‡ |
| 6912 | 3072 | 12288 | 128 | 1 | 76.83 | 76.90 | 0.999 ‡ |
| 4096 | 3072 | 3072 | 32 | 1 | 18.46 | 18.46 | 1.000 ‡ |
| 4096 | 3072 | 12288 | 32 | 1 | 49.79 | 49.79 | 1.000 ‡ |
| 4096 | 12288 | 3072 | 32 | 1 | 50.72 | 50.75 | 0.999 ‡ |
| 6889 | 3072 | 3072 | 32 | 1 | 25.86 | 25.82 | 1.002 ‡ |
| 6889 | 3072 | 12288 | 32 | 1 | 74.96 | 74.94 | 1.000 ‡ |
| 6889 | 12288 | 3072 | 32 | 1 | 79.20 | 79.36 | 0.998 ‡ |
| 9216 | 3072 | 3072 | 32 | 1 | 31.65 | 31.62 | 1.001 ‡ |
| 9216 | 3072 | 12288 | 32 | 1 | 93.57 | 93.57 | 1.000 ‡ |
| 9216 | 12288 | 3072 | 32 | 1 | 103.76 | 103.82 | 0.999 ‡ |
| 16384 | 3072 | 3072 | 32 | 1 | 49.92 | 49.89 | 1.001 ‡ |
| 16384 | 3072 | 12288 | 32 | 1 | 161.30 | 161.39 | 0.999 ‡ |
| 16384 | 12288 | 3072 | 32 | 1 | 181.44 | 181.52 | 1.000 ‡ |

‡ This shape dispatches to the same kernel build as the previous Cake
release on this GPU; its ratio is that session's same-build reading.

**Speedup table on NVIDIA GB200 (sm_100a), CUDA 13.4, median kernel time
(CUPTI, cold L2), session s14** — every shape keeps its previous kernel
build on this GPU

| M | N | K | rank | bias | previous Cake (µs) | this PR (µs) | speedup
vs previous Cake |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 129 | 3072 | 3072 | 32 | 1 | 5.95 | 5.95 | 1.000 ‡ |
| 129 | 3072 | 3072 | 32 | 0 | 5.89 | 5.89 | 1.000 ‡ |
| 129 | 3072 | 3072 | 64 | 1 | 6.05 | 6.02 | 1.005 ‡ |
| 129 | 3072 | 3072 | 96 | 1 | 6.14 | 6.14 | 1.000 ‡ |
| 129 | 3072 | 3072 | 128 | 1 | 6.18 | 6.18 | 1.000 ‡ |
| 129 | 3072 | 3072 | 128 | 0 | 6.11 | 6.14 | 0.995 ‡ |
| 129 | 3072 | 12288 | 32 | 0 | 11.04 | 11.04 | 1.000 ‡ |
| 129 | 3072 | 12288 | 32 | 1 | 11.04 | 11.04 | 1.000 ‡ |
| 129 | 3072 | 12288 | 128 | 0 | 11.14 | 11.14 | 1.000 ‡ |
| 129 | 3072 | 12288 | 128 | 1 | 11.14 | 11.14 | 1.000 ‡ |
| 6912 | 3072 | 3072 | 32 | 1 | 28.54 | 28.74 | 0.993 ‡ |
| 6912 | 3072 | 3072 | 64 | 1 | 28.94 | 29.02 | 0.997 ‡ |
| 6912 | 3072 | 3072 | 96 | 1 | 30.30 | 30.26 | 1.001 ‡ |
| 6912 | 3072 | 3072 | 128 | 1 | 31.10 | 31.27 | 0.995 ‡ |
| 6912 | 3072 | 12288 | 32 | 1 | 97.65 | 97.62 | 1.000 ‡ |
| 6912 | 3072 | 12288 | 128 | 1 | 100.03 | 100.00 | 1.000 ‡ |
| 4096 | 3072 | 3072 | 32 | 1 | 19.55 | 19.55 | 1.000 ‡ |
| 4096 | 3072 | 12288 | 32 | 1 | 62.86 | 62.77 | 1.001 ‡ |
| 4096 | 12288 | 3072 | 32 | 1 | 63.76 | 63.76 | 1.000 ‡ |
| 6889 | 3072 | 3072 | 32 | 1 | 28.37 | 28.20 | 1.006 ‡ |
| 6889 | 3072 | 12288 | 32 | 1 | 97.76 | 97.60 | 1.002 ‡ |
| 6889 | 12288 | 3072 | 32 | 1 | 106.00 | 106.08 | 0.999 ‡ |
| 9216 | 3072 | 3072 | 32 | 1 | 35.54 | 35.52 | 1.001 ‡ |
| 9216 | 3072 | 12288 | 32 | 1 | 122.75 | 122.70 | 1.000 ‡ |
| 9216 | 12288 | 3072 | 32 | 1 | 134.64 | 134.77 | 0.999 ‡ |
| 16384 | 3072 | 3072 | 32 | 1 | 64.32 | 64.26 | 1.001 ‡ |
| 16384 | 3072 | 12288 | 32 | 1 | 205.95 | 205.78 | 1.001 ‡ |
| 16384 | 12288 | 3072 | 32 | 1 | 232.97 | 232.53 | 1.002 ‡ |

‡ This shape dispatches to the same kernel build as the previous Cake
release on this GPU; its ratio is that session's same-build reading.

Cake ships no other data-type, layout or fused-form variant of this
kernel beyond the one above (with and without the fused bias, LoRA ranks
32 / 64 / 96 / 128), and the family ships on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized NVFP4 SVD-quantized GEMM kernel options for SM103a
GPUs, including coverage for additional matrix shapes and
configurations.
* **Improvements**
* Updated automatic kernel selection for supported SM103a workloads,
including configurations with and without bias.
* Refined GPU synchronization and memory-transfer behavior across kernel
variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [1b09e8d](https://github.com/flashinfer-ai/flashinfer/commit/1b09e8d1c4562ecd09840a959ff771e09907cab6)

- **作者**: eigen
- **时间**: 2026-10-24T22:21:08Z
- **提交信息**: perf(cake_gdp): issue the dense v / beta row loads at the k load site in the one-row-per-thread T = 1 decode kernels on SM100 / SM103 (#7178)

The Cake Gated DeltaProduct decode kernel
(`flashinfer.cake_gdp.cake_gated_delta_product_mtp`) has one variant:
BF16 q / k / v / output with an FP32 recurrent state in a slot-indexed
state pool, float32 `A_log` and `dt_bias`, optional per-token state
scatter, 1 <= T <= 16 tokens per sequence, K = 128, V = 64 and 1 <= n <=
4 Householder sub-steps. This PR delivers that same variant with a
change inside the T = 1 one-row-per-thread kernels on sm_100a / sm_103a
(four programs on each architecture): these kernels now issue the dense
v / beta row loads at the k load site in register form and defer the
unpack until after the slot test and the state accesses are issued, so
the row loads overlap the slot test and the state traffic instead of
waiting behind them. The operands and their order are the same, so
outputs and state writes are equal to those of the previous package; the
registry, the host plan, the kernel selection rule and the public API
are unchanged, and the T = 1 split-V kernel, the T = 4 / T = 8 kernels
and every sm_90a kernel compile to the same SASS as in the previous
package (the only source changes are inside the T = 1 one-row-per-thread
kernels on sm_100a / sm_103a). The baseline is the previous Cake version
of this kernel, the Cake GDP decode package of FlashInfer PR #7156,
whose head is the direct predecessor of this package; both packages ran
in the same process on the same GPU with the same inputs, interleaved A
B B A over 3 groups x 32 samples per call, with cold L2 and kernel time
measured, and speedup = previous / this PR is 0.99-1.08 on GB300 and
0.98-1.09 on B200 across the 48 shapes (HV in {80, 20, 10, 24} x B in
{1, 16, 64, 256} x T in {1, 4, 8}, n = 3). The changed kernels run on
the eleven T = 1 rows outside the five split-V rows (B = 1 for every HV,
and HV 10 x B 16): six of them move (HV 80 x B 16, HV 20 x B 16, HV 20 x
B 64, HV 10 x B 256, HV 24 x B 16, HV 24 x B 64), at 1.02-1.08 on GB300
and 1.03-1.09 on B200, and the other five read 1.00 on both GPUs; the
split-V rows and every T = 4 / T = 8 row run unchanged kernels.

**NVIDIA GB300 (sm_103a), CUDA 13.4.92 -- 48 rows, speedup 0.99-1.08**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.0 | 4.0 | 1.00 |
| 80 | 1 | 4 | 6.0 | 6.0 | 0.99 |
| 80 | 1 | 8 | 8.1 | 8.1 | 1.01 |
| 80 | 16 | 1 | 17.6 | 17.0 | 1.03 |
| 80 | 16 | 4 | 24.8 | 24.7 | 1.00 |
| 80 | 16 | 8 | 40.0 | 40.0 | 1.00 |
| 80 | 64 | 1 | 54.9 | 55.1 | 1.00 |
| 80 | 64 | 4 | 75.9 | 75.9 | 1.00 |
| 80 | 64 | 8 | 131.2 | 131.2 | 1.00 |
| 80 | 256 | 1 | 198.7 | 199.2 | 1.00 |
| 80 | 256 | 4 | 281.7 | 281.8 | 1.00 |
| 80 | 256 | 8 | 499.2 | 499.2 | 1.00 |
| 20 | 1 | 1 | 3.2 | 3.2 | 1.00 |
| 20 | 1 | 4 | 5.5 | 5.5 | 1.00 |
| 20 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 20 | 16 | 1 | 7.3 | 7.1 | 1.03 |
| 20 | 16 | 4 | 10.9 | 11.0 | 0.99 |
| 20 | 16 | 8 | 16.5 | 16.6 | 1.00 |
| 20 | 64 | 1 | 17.7 | 17.0 | 1.04 |
| 20 | 64 | 4 | 24.6 | 24.5 | 1.00 |
| 20 | 64 | 8 | 39.9 | 40.0 | 1.00 |
| 20 | 256 | 1 | 55.0 | 55.2 | 1.00 |
| 20 | 256 | 4 | 75.9 | 76.1 | 1.00 |
| 20 | 256 | 8 | 131.3 | 131.2 | 1.00 |
| 10 | 1 | 1 | 3.2 | 3.2 | 1.00 |
| 10 | 1 | 4 | 5.4 | 5.4 | 1.00 |
| 10 | 1 | 8 | 7.5 | 7.5 | 1.00 |
| 10 | 16 | 1 | 5.1 | 5.0 | 1.01 |
| 10 | 16 | 4 | 8.2 | 8.1 | 1.01 |
| 10 | 16 | 8 | 11.9 | 12.0 | 1.00 |
| 10 | 64 | 1 | 11.1 | 11.0 | 1.00 |
| 10 | 64 | 4 | 16.0 | 16.0 | 1.00 |
| 10 | 64 | 8 | 24.9 | 25.2 | 0.99 |
| 10 | 256 | 1 | 30.0 | 29.5 | 1.02 |
| 10 | 256 | 4 | 41.4 | 41.5 | 1.00 |
| 10 | 256 | 8 | 69.5 | 69.5 | 1.00 |
| 24 | 1 | 1 | 3.3 | 3.3 | 0.99 |
| 24 | 1 | 4 | 5.5 | 5.6 | 1.00 |
| 24 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 24 | 16 | 1 | 7.8 | 7.5 | 1.04 |
| 24 | 16 | 4 | 11.4 | 11.4 | 1.00 |
| 24 | 16 | 8 | 17.2 | 17.2 | 1.00 |
| 24 | 64 | 1 | 20.5 | 18.9 | 1.08 |
| 24 | 64 | 4 | 28.1 | 28.3 | 0.99 |
| 24 | 64 | 8 | 46.9 | 46.9 | 1.00 |
| 24 | 256 | 1 | 64.5 | 64.8 | 1.00 |
| 24 | 256 | 4 | 89.9 | 90.0 | 1.00 |
| 24 | 256 | 8 | 156.3 | 156.2 | 1.00 |

**NVIDIA B200 (sm_100a), CUDA 13.4.92 -- 48 rows, speedup 0.98-1.09**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.2 | 4.2 | 1.00 |
| 80 | 1 | 4 | 6.3 | 6.3 | 1.00 |
| 80 | 1 | 8 | 8.5 | 8.6 | 1.00 |
| 80 | 16 | 1 | 18.8 | 17.5 | 1.08 |
| 80 | 16 | 4 | 26.5 | 26.6 | 1.00 |
| 80 | 16 | 8 | 43.6 | 43.6 | 1.00 |
| 80 | 64 | 1 | 57.2 | 57.2 | 1.00 |
| 80 | 64 | 4 | 83.2 | 83.2 | 1.00 |
| 80 | 64 | 8 | 144.8 | 144.8 | 1.00 |
| 80 | 256 | 1 | 205.0 | 204.8 | 1.00 |
| 80 | 256 | 4 | 306.2 | 306.1 | 1.00 |
| 80 | 256 | 8 | 543.9 | 544.1 | 1.00 |
| 20 | 1 | 1 | 3.4 | 3.4 | 1.00 |
| 20 | 1 | 4 | 5.8 | 5.8 | 1.00 |
| 20 | 1 | 8 | 8.0 | 8.1 | 1.00 |
| 20 | 16 | 1 | 7.8 | 7.6 | 1.03 |
| 20 | 16 | 4 | 11.6 | 11.6 | 1.00 |
| 20 | 16 | 8 | 17.9 | 17.9 | 1.00 |
| 20 | 64 | 1 | 18.4 | 17.8 | 1.03 |
| 20 | 64 | 4 | 26.6 | 26.8 | 0.99 |
| 20 | 64 | 8 | 43.6 | 43.6 | 1.00 |
| 20 | 256 | 1 | 57.2 | 57.3 | 1.00 |
| 20 | 256 | 4 | 83.3 | 83.3 | 1.00 |
| 20 | 256 | 8 | 144.8 | 144.9 | 1.00 |
| 10 | 1 | 1 | 3.3 | 3.3 | 1.01 |
| 10 | 1 | 4 | 5.6 | 5.6 | 1.00 |
| 10 | 1 | 8 | 7.9 | 7.9 | 1.00 |
| 10 | 16 | 1 | 5.3 | 5.2 | 1.03 |
| 10 | 16 | 4 | 8.6 | 8.5 | 1.01 |
| 10 | 16 | 8 | 12.8 | 12.7 | 1.01 |
| 10 | 64 | 1 | 11.8 | 11.7 | 1.00 |
| 10 | 64 | 4 | 16.8 | 17.0 | 0.98 |
| 10 | 64 | 8 | 27.4 | 27.2 | 1.00 |
| 10 | 256 | 1 | 31.4 | 30.5 | 1.03 |
| 10 | 256 | 4 | 45.9 | 45.8 | 1.00 |
| 10 | 256 | 8 | 78.3 | 78.3 | 1.00 |
| 24 | 1 | 1 | 3.4 | 3.4 | 1.00 |
| 24 | 1 | 4 | 5.8 | 5.8 | 1.01 |
| 24 | 1 | 8 | 8.0 | 8.0 | 1.00 |
| 24 | 16 | 1 | 8.2 | 7.9 | 1.03 |
| 24 | 16 | 4 | 12.1 | 12.1 | 0.99 |
| 24 | 16 | 8 | 18.4 | 18.5 | 1.00 |
| 24 | 64 | 1 | 21.5 | 19.7 | 1.09 |
| 24 | 64 | 4 | 30.4 | 30.5 | 1.00 |
| 24 | 64 | 8 | 51.2 | 51.3 | 1.00 |
| 24 | 256 | 1 | 66.7 | 66.8 | 1.00 |
| 24 | 256 | 4 | 98.3 | 98.5 | 1.00 |
| 24 | 256 | 8 | 171.8 | 171.6 | 1.00 |

This variant is the kernel family's only data-type form; Cake ships it
on sm_90a (H100 / H200), sm_100a (B200 / GB200) and sm_103a (B300 /
GB300), and this PR changes eight sm_100a / sm_103a kernels (the four T
= 1 one-row-per-thread programs on each architecture) and adds none.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated Cake GDP decoding across supported GPU architectures,
including bfloat16 input handling and calculation paths.
* Aligned parameter handling with the updated processing order while
retaining architecture-specific behavior.
* **Tests**
* Updated alignment checks to verify that selected inputs are accessed
in 2-byte units.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [809870c](https://github.com/flashinfer-ai/flashinfer/commit/809870c14cc33a9081704658285ef2307a7e03e6)

- **作者**: eigen
- **时间**: 2026-10-24T22:20:55Z
- **提交信息**: feat(cake_muse_spark_norm): deliver the sm_107a programs and cache launch plans per call signature (#7177)

This PR adds the `sm_107a` (NVIDIA R200) programs and routes to
`cake_muse_spark_norm_backend`, the Cake backend for three fused RMSNorm
ops that FlashInfer already exposes:
`flashinfer.norm.gated_residual_rmsnorm`,
`flashinfer.norm.gated_residual_next_rmsnorm` and
`flashinfer.norm.rmsnorm_sigmoid_gate`. The backend already ships on
`sm_100a` (NVIDIA B200) and `sm_103a` (NVIDIA GB300) from PR #7119.
Before this PR, `sm_107a` was an exported target with no routed program.
The timed variants are the same as in #7119. `gated_residual_rmsnorm`
uses hidden 8192, BF16 `branch`, FP32 `residual` / `alpha` / `beta` /
`out`, and runtime `eps` and `gain_center`. It has two modes over M
rows: mode 0 has no weight, and mode 1 applies a weight before the norm.
`gated_residual_next_rmsnorm` uses hidden 8192, FP32 `residual_out` and
BF16 `ffn_input`. It is timed in two forms over M rows: V1 uses an alpha
tensor and `post_weight`, and V2 uses scalar alpha 1.0 without
`post_weight`. `rmsnorm_sigmoid_gate` normalizes per-(token, head) rows
of 64 BF16 values in place and reads the gate from a strided view of the
projection. It is timed at 128, 32 and 16 heads over T tokens. No
earlier Cake version of these kernels has shipped on `sm_107a`, so the
baseline is FlashInfer's existing CuTe DSL kernels (PR #6544), run
through the same public API on the same GPU in the same process. Speedup
= baseline µs / Cake µs, and a value above 1 means Cake is faster.

**`gated_residual_rmsnorm`, NVIDIA R200 (`sm_107a`, 212 SMs), CUDA
13.0.** M ≤ 128: CUDA graph of 32 launches replayed with PDL on both
sides, per-launch average; M ≥ 256: isolated launch, cold L2 (CUPTI
kernel-active median). Rows marked `same kernel` route to the existing
CuTe kernel on this architecture.

| mode | M | baseline µs | Cake µs | speedup |
|---:|---:|---:|---:|---:|
| 0 | 1 | 1.31 | 1.08 | 1.206 |
| 0 | 2 | 1.31 | 1.12 | 1.162 |
| 0 | 4 | 1.31 | 1.13 | 1.162 |
| 0 | 8 | 1.34 | 1.16 | 1.151 |
| 0 | 16 | 1.43 | 1.20 | 1.189 |
| 0 | 32 | 1.45 | 1.33 | 1.089 |
| 0 | 64 | 1.81 | 1.67 | 1.084 |
| 0 | 128 | 2.05 | 1.93 | 1.060 |
| 0 | 256 | 3.87 | same kernel | — |
| 0 | 1024 | 9.92 | 9.22 | 1.076 |
| 0 | 2048 | 16.77 | 15.90 | 1.054 |
| 0 | 4096 | 30.72 | 29.34 | 1.047 |
| 0 | 8192 | 59.04 | 56.26 | 1.049 |
| 0 | 16384 | 112.27 | 111.36 | 1.008 |
| 1 | 1 | 1.40 | 1.26 | 1.113 |
| 1 | 2 | 1.42 | 1.36 | 1.047 |
| 1 | 4 | 1.39 | 1.30 | 1.068 |
| 1 | 8 | 1.42 | 1.23 | 1.156 |
| 1 | 16 | 1.59 | 1.50 | 1.062 |
| 1 | 32 | 1.64 | 1.58 | 1.035 |
| 1 | 64 | 2.07 | 1.87 | 1.095 |
| 1 | 128 | 2.23 | 2.03 | 1.100 |
| 1 | 256 | 4.61 | 4.27 | 1.079 |
| 1 | 1024 | 11.26 | 9.31 | 1.210 |
| 1 | 2048 | 18.30 | 15.89 | 1.152 |
| 1 | 4096 | 34.05 | 29.10 | 1.170 |
| 1 | 8192 | 64.16 | 56.38 | 1.138 |
| 1 | 16384 | 123.09 | 113.07 | 1.089 |

**`gated_residual_next_rmsnorm`, NVIDIA R200 (`sm_107a`, 212 SMs), CUDA
13.0.** Isolated launch, cold L2 (CUPTI kernel-active median).

| variant | M | baseline µs | Cake µs | speedup |
|---:|---:|---:|---:|---:|
| V1 | 1 | 2.46 | 2.24 | 1.096 |
| V1 | 8 | 2.85 | 2.58 | 1.106 |
| V1 | 16 | 2.96 | 2.69 | 1.101 |
| V1 | 32 | 3.10 | 2.85 | 1.090 |
| V1 | 64 | 3.39 | 3.06 | 1.110 |
| V1 | 128 | 4.34 | 3.68 | 1.178 |
| V1 | 256 | 7.37 | 4.94 | 1.493 |
| V1 | 512 | 11.48 | 7.46 | 1.538 |
| V1 | 1024 | 20.61 | 11.65 | 1.769 |
| V1 | 2048 | 38.34 | 19.27 | 1.989 |
| V1 | 4096 | 74.26 | 33.46 | 2.220 |
| V1 | 8192 | 145.41 | 63.26 | 2.299 |
| V1 | 16384 | 288.40 | 126.02 | 2.288 |
| V2 | 1 | 2.43 | 2.11 | 1.152 |
| V2 | 8 | 2.77 | 2.51 | 1.102 |
| V2 | 16 | 2.82 | 2.56 | 1.100 |
| V2 | 32 | 3.02 | 2.77 | 1.092 |
| V2 | 64 | 3.31 | 3.00 | 1.104 |
| V2 | 128 | 4.26 | 3.61 | 1.180 |
| V2 | 256 | 7.26 | 4.87 | 1.491 |
| V2 | 512 | 11.15 | 6.94 | 1.608 |
| V2 | 1024 | 19.83 | 11.10 | 1.787 |
| V2 | 2048 | 36.63 | 18.94 | 1.934 |
| V2 | 4096 | 70.83 | 34.77 | 2.037 |
| V2 | 8192 | 139.34 | 66.08 | 2.109 |
| V2 | 16384 | 276.34 | 128.03 | 2.158 |

**`rmsnorm_sigmoid_gate`, NVIDIA R200 (`sm_107a`, 212 SMs), CUDA 13.0.**
Isolated launch, cold L2 (CUPTI kernel-active median). Rows marked `same
kernel` route to the existing CuTe kernel on this architecture.

| heads | T | baseline µs | Cake µs | speedup |
|---:|---:|---:|---:|---:|
| 128 | 1 | 1.43 | same kernel | — |
| 128 | 2 | 1.86 | 1.73 | 1.077 |
| 128 | 3 | 1.75 | same kernel | — |
| 128 | 8 | 1.79 | same kernel | — |
| 128 | 64 | 2.14 | 2.13 | 1.006 |
| 128 | 256 | 3.32 | 3.14 | 1.056 |
| 128 | 1024 | 8.20 | 7.98 | 1.028 |
| 128 | 4096 | 26.67 | 25.04 | 1.065 |
| 128 | 16384 | 99.71 | 91.86 | 1.085 |
| 32 | 1 | 1.39 | 1.30 | 1.071 |
| 32 | 2 | 1.81 | 1.47 | 1.235 |
| 32 | 8 | 1.86 | 1.49 | 1.254 |
| 32 | 9 | 1.73 | 1.47 | 1.180 |
| 32 | 17 | 1.76 | same kernel | — |
| 32 | 64 | 1.85 | same kernel | — |
| 32 | 256 | 2.15 | 2.14 | 1.006 |
| 32 | 257 | 2.15 | same kernel | — |
| 32 | 1024 | 3.32 | same kernel | — |
| 32 | 4096 | 8.19 | 7.96 | 1.028 |
| 32 | 16384 | 26.62 | 25.02 | 1.064 |
| 16 | 1 | 1.39 | 1.21 | 1.144 |
| 16 | 8 | 1.85 | 1.47 | 1.263 |
| 16 | 16 | 1.90 | 1.48 | 1.283 |
| 16 | 17 | 2.27 | 1.70 | 1.338 |
| 16 | 64 | 2.36 | 1.81 | 1.301 |
| 16 | 256 | 2.49 | 1.99 | 1.251 |
| 16 | 1024 | 2.97 | 2.37 | 1.253 |
| 16 | 4096 | 6.39 | 4.86 | 1.314 |
| 16 | 16384 | 18.82 | 13.25 | 1.420 |

Besides the variants timed above, the package also serves two more forms
of `gated_residual_next_rmsnorm` (scalar alpha with `post_weight`, and
alpha tensor without `post_weight`) and the PDL builds of the
`gated_residual_rmsnorm` programs; this family ships on `sm_100a`
(B200), `sm_103a` (GB300) and, with this PR, `sm_107a` (R200).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added Cake backend support for gated residual RMSNorm, gated residual
next-RMSNorm, and RMSNorm with sigmoid gating on supported GPUs.
* Added automatic backend selection with CuTe fallback when Cake does
not support the requested shape. Users can also select a backend
explicitly.
* Added support checks for operation variants and shape ranges, plus
improved handling of empty batches.
* **Bug Fixes**
* Improved validation of tensor layouts and supported shapes, with
clearer errors for unsupported inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7bc25aa](https://github.com/flashinfer-ai/flashinfer/commit/7bc25aaefe1e5bf16c8e35e5604c392c8086ef8a)

- **作者**: eigen
- **时间**: 2026-10-24T22:20:37Z
- **提交信息**: perf(cake_kda): auto grad, ship the BF16x3 half-width transfer walk on the context-parallel route (#7176)

The Cake packed KDA kernels form a chunked training backend for
documents packed into one sequence and come in two Cake variants: a
single-device packed training variant, and a context-parallel (KCP)
variant that splits the sequence over the ranks of a torch.distributed
group, passes the recurrent state between ranks through FP32 affine
state summaries, and supports contiguous, zigzag and per-document zigzag
+ ragged partition layouts with saved-context and checkpoint-replay
backward. This PR gives the context-parallel variant a faster cross-rank
state transfer: the transfer walk, which carries the FP32 recurrent
state across fragment boundaries and ranks as the affine product S_out =
M * S_in + B, now computes a half-width BF16x3 split product (each FP32
operand split into three BF16 parts, products on the tensor cores, FP32
accumulation) with two CTAs per (segment, head), each covering one half
of the state's columns, in place of the previous full-width TF32 hi/lo
split product with one CTA per (segment, head). M, B and the states keep
FP32 storage, and every other kernel, the single-device path, the
partition layouts and both backward modes are unchanged; results differ
from the previous version only in the last bits of the transferred state
(a different product rounding) and stay inside the family's
FP64-referenced precision budgets, and forward and backward are bitwise
reproducible run to run. Against the previous Cake version of the same
kernels as merged in PR #7117, measured as an interleaved arm in the
same sessions with the same protocol, the speedup ranges from 0.9498x to
1.0868x in session 1 and from 0.9812x to 1.0560x in session 2; 89 of 144
rows are faster by more than 2 % in both sessions, 39 of 144 stay within
0.98-1.02 in both, none of the 144 is slower by more than 2 % in both,
and the remaining rows change band between the sessions. Two rows are
slower than the previous version by more than 2 % in session 1 only and
faster in session 2: Q2 CP8 contiguous B1 (0.9498x / 1.0268x) and Q4 CP8
zigzag B3 (0.9576x / 1.0127x). The transfer walk is a forward-side cost,
so the gain shows most in B1, the module forward, which ranges from
0.9498x to 1.0868x across both sessions and is above 1.02x in every CP2
row, with the largest single-row ratios and the widest spread at CP8 /
CP16, while B3, which adds checkpoint replay and the unchanged backward,
ranges from 0.9576x to 1.0233x.

Measured on NVIDIA GB300 (sm_103a) with CUDA 13.0, driver 580.159.03 and
NCCL 2.30.7; latency in ms = median over steady iterations of the
slowest rank, from two independent sessions s1 / s2 on different nodes,
and speedup = previous version ms / this PR ms; CP2 / CP4 on one node of
4 GPUs, CP8 on two nodes, CP16 on four nodes of one NVL72 domain; B1 =
module forward (conv halo + conv + KDA state passing + recurrence,
communication included), B3 = forward + checkpoint replay + backward;
previous version = the same kernels as merged in PR #7117, run as an
interleaved arm in the same sessions with the same protocol.

| pack | CP | layout | boundary | previous version ms (s1 / s2) | this
PR ms (s1 / s2) | speedup vs previous version (s1 / s2) |
|---|---|---|---|---|---|---|
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B1 = forward | 15.956 /
15.927 | 15.324 / 15.282 | 1.0412 / 1.0422 |
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 65.367 / 65.321 | 64.060 / 64.027 | 1.0204 / 1.0202
|
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B1 = forward | 16.137 /
16.129 | 15.524 / 15.487 | 1.0395 / 1.0415 |
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 65.887 / 65.911 | 64.677 / 64.681 | 1.0187 / 1.0190
|
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.201 / 16.168 | 15.565 / 15.529 | 1.0409 / 1.0411 |
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 66.019 / 65.997 | 64.725 /
64.696 | 1.0200 / 1.0201 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B1 = forward | 14.461 /
14.427 | 14.105 / 14.081 | 1.0252 / 1.0246 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 58.905 / 58.910 | 58.258 / 58.203 | 1.0111 / 1.0121
|
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B1 = forward | 15.266 /
15.249 | 14.630 / 14.595 | 1.0435 / 1.0448 |
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 61.498 / 61.492 | 60.182 / 60.168 | 1.0219 / 1.0220
|
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 14.984 / 14.947 | 14.370 / 14.324 | 1.0427 / 1.0435 |
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 60.877 / 60.892 | 59.645 /
59.585 | 1.0207 / 1.0219 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B1 = forward | 16.579 /
16.542 | 15.882 / 15.839 | 1.0439 / 1.0444 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 67.956 / 67.899 | 66.516 / 66.484 | 1.0216 / 1.0213
|
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B1 = forward | 16.392 /
16.370 | 15.739 / 15.718 | 1.0415 / 1.0415 |
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 67.568 / 67.537 | 66.269 / 66.220 | 1.0196 / 1.0199
|
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 17.197 / 17.184 | 16.547 / 16.493 | 1.0393 / 1.0419 |
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 69.886 / 69.898 | 68.498 /
68.459 | 1.0203 / 1.0210 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B1 = forward | 15.074 /
15.056 | 14.460 / 14.430 | 1.0425 / 1.0434 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 62.207 / 62.171 | 60.988 / 60.948 | 1.0200 / 1.0201
|
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B1 = forward | 15.188 /
15.148 | 14.636 / 14.592 | 1.0377 / 1.0381 |
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 62.333 / 62.317 | 61.361 / 61.251 | 1.0158 / 1.0174
|
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 15.855 / 15.839 | 15.208 / 15.190 | 1.0425 / 1.0427 |
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 64.450 / 64.483 | 63.183 /
63.128 | 1.0201 / 1.0215 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B1 = forward | 16.178 /
16.141 | 15.442 / 15.433 | 1.0477 / 1.0459 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 66.245 / 66.164 | 64.833 / 64.774 | 1.0218 / 1.0215
|
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B1 = forward | 16.049 /
16.018 | 15.421 / 15.364 | 1.0407 / 1.0426 |
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 65.990 / 65.953 | 64.804 / 64.695 | 1.0183 / 1.0194
|
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.584 / 16.575 | 15.913 / 15.929 | 1.0422 / 1.0406 |
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 67.604 / 67.637 | 66.273 /
66.279 | 1.0201 / 1.0205 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B1 = forward | 16.147 /
16.134 | 15.506 / 15.493 | 1.0413 / 1.0414 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 65.686 / 65.674 | 64.401 / 64.361 | 1.0200 / 1.0204
|
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B1 = forward | 16.419 /
16.407 | 15.767 / 15.729 | 1.0414 / 1.0431 |
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 66.615 / 66.596 | 65.325 / 65.306 | 1.0197 / 1.0198
|
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.909 / 16.879 | 16.207 / 16.181 | 1.0433 / 1.0431 |
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 68.584 / 68.514 | 67.164 /
67.131 | 1.0211 / 1.0206 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B1 = forward | 8.271 /
8.274 | 8.000 / 7.999 | 1.0339 / 1.0344 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 33.410 / 33.421 | 32.889 / 32.899 | 1.0158 / 1.0159
|
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B1 = forward | 8.524 / 8.512
| 8.196 / 8.196 | 1.0400 / 1.0386 |
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 34.117 / 34.115 | 33.489 / 33.511 | 1.0188 / 1.0180
|
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.393 / 8.402 | 8.002 / 7.985 | 1.0489 / 1.0522 |
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 33.870 / 33.918 | 33.142 /
33.163 | 1.0220 / 1.0228 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B1 = forward | 7.629 /
7.622 | 7.467 / 7.432 | 1.0217 / 1.0256 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 30.439 / 30.455 | 30.053 / 30.031 | 1.0128 / 1.0141
|
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B1 = forward | 7.864 / 7.862
| 7.566 / 7.552 | 1.0394 / 1.0410 |
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 31.234 / 31.295 | 30.674 / 30.695 | 1.0183 / 1.0195
|
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 7.796 / 7.778 | 7.507 / 7.493 | 1.0385 / 1.0380 |
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 31.241 / 31.260 | 30.702 /
30.712 | 1.0176 / 1.0178 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B1 = forward | 8.671 /
8.666 | 8.299 / 8.276 | 1.0448 / 1.0471 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 35.034 / 35.045 | 34.289 / 34.309 | 1.0217 / 1.0215
|
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B1 = forward | 8.898 / 8.893
| 8.544 / 8.571 | 1.0414 / 1.0376 |
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 35.681 / 35.663 | 34.991 / 35.085 | 1.0197 / 1.0165
|
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.816 / 8.828 | 8.475 / 8.997 | 1.0402 / 0.9812 |
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 35.656 / 35.676 | 34.953 /
34.979 | 1.0201 / 1.0199 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B1 = forward | 8.127 /
8.117 | 7.904 / 8.269 | 1.0282 / 0.9816 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 32.502 / 32.484 | 32.022 / 32.023 | 1.0150 / 1.0144
|
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B1 = forward | 8.263 / 8.260
| 7.892 / 7.879 | 1.0470 / 1.0484 |
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 32.958 / 32.982 | 32.266 / 32.279 | 1.0214 / 1.0218
|
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.358 / 8.355 | 8.063 / 8.055 | 1.0366 / 1.0372 |
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 33.384 / 33.413 | 32.778 /
32.813 | 1.0185 / 1.0183 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B1 = forward | 8.463 /
8.452 | 8.107 / 8.090 | 1.0439 / 1.0447 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 34.166 / 34.165 | 33.437 / 33.425 | 1.0218 / 1.0221
|
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B1 = forward | 8.716 / 8.725
| 8.364 / 8.376 | 1.0421 / 1.0417 |
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 34.942 / 34.970 | 34.255 / 34.288 | 1.0201 / 1.0199
|
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.604 / 8.609 | 8.240 / 8.229 | 1.0442 / 1.0462 |
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 34.792 / 34.786 | 34.051 /
34.042 | 1.0218 / 1.0219 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B1 = forward | 8.336 /
8.308 | 8.116 / 8.097 | 1.0271 / 1.0261 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 33.469 / 33.474 | 33.065 / 33.055 | 1.0122 / 1.0127
|
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B1 = forward | 8.467 / 8.469
| 8.199 / 8.202 | 1.0327 / 1.0326 |
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 33.972 / 34.027 | 33.421 / 33.425 | 1.0165 / 1.0180
|
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.774 / 8.763 | 8.435 / 8.402 | 1.0402 / 1.0430 |
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 34.970 / 34.969 | 34.276 /
34.295 | 1.0202 / 1.0197 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B1 = forward | 4.619 /
4.624 | 4.443 / 4.450 | 1.0396 / 1.0391 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 17.936 / 17.949 | 17.616 / 17.632 | 1.0182 / 1.0180
|
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B1 = forward | 4.835 / 4.573
| 4.449 / 4.454 | 1.0868 / 1.0267 |
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.930 / 17.933 | 17.695 / 17.687 | 1.0133 / 1.0139
|
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.694 / 4.697 | 4.488 / 4.512 | 1.0459 / 1.0410 |
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.420 / 18.387 | 18.075 /
18.023 | 1.0191 / 1.0202 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.273 /
4.285 | 4.499 / 4.173 | 0.9498 / 1.0268 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 16.465 / 16.465 | 16.233 / 16.224 | 1.0143 / 1.0149
|
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.230 / 4.219
| 4.133 / 4.102 | 1.0235 / 1.0285 |
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 16.404 / 16.410 | 16.207 / 16.211 | 1.0122 / 1.0123
|
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.282 / 4.236 | 4.107 / 4.080 | 1.0426 / 1.0382 |
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 16.668 / 16.640 | 16.363 /
16.326 | 1.0186 / 1.0192 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B1 = forward | 4.794 /
4.804 | 4.659 / 4.660 | 1.0290 / 1.0309 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.693 / 18.715 | 18.422 / 18.436 | 1.0147 / 1.0151
|
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B1 = forward | 4.782 / 4.768
| 4.837 / 4.648 | 0.9886 / 1.0258 |
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 18.746 / 18.765 | 18.490 / 18.520 | 1.0138 / 1.0132
|
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.934 / 4.937 | 4.738 / 4.747 | 1.0414 / 1.0400 |
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 19.315 / 19.331 | 18.933 /
18.945 | 1.0202 / 1.0204 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B1 = forward | 4.510 /
4.488 | 4.312 / 4.301 | 1.0459 / 1.0435 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 17.367 / 17.358 | 17.030 / 17.006 | 1.0198 / 1.0207
|
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B1 = forward | 4.443 / 4.425
| 4.327 / 4.310 | 1.0268 / 1.0267 |
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.304 / 17.299 | 18.071 / 17.082 | 0.9576 / 1.0127
|
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.509 / 4.503 | 4.336 / 4.325 | 1.0399 / 1.0412 |
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 17.566 / 17.582 | 17.214 /
17.212 | 1.0204 / 1.0215 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B1 = forward | 4.692 /
4.684 | 4.554 / 4.562 | 1.0303 / 1.0267 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.238 / 18.254 | 17.980 / 17.989 | 1.0143 / 1.0147
|
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B1 = forward | 4.677 / 4.670
| 4.540 / 4.551 | 1.0302 / 1.0261 |
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 18.322 / 18.347 | 18.076 / 18.102 | 1.0136 / 1.0135
|
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.896 / 4.876 | 4.685 / 4.683 | 1.0450 / 1.0412 |
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 19.224 / 19.205 | 18.820 /
18.790 | 1.0215 / 1.0221 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.628 /
4.605 | 4.501 / 4.481 | 1.0282 / 1.0277 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 17.946 / 17.930 | 17.693 / 17.700 | 1.0143 / 1.0130
|
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.584 / 4.574
| 4.457 / 4.458 | 1.0285 / 1.0260 |
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.907 / 17.905 | 17.677 / 17.680 | 1.0130 / 1.0127
|
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.639 / 4.657 | 4.482 / 4.497 | 1.0350 / 1.0356 |
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.302 / 18.314 | 17.980 /
18.028 | 1.0179 / 1.0159 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B1 = forward | 2.721 /
2.745 | 2.579 / 2.608 | 1.0551 / 1.0525 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.848 / 9.884 | 9.644 / 9.674 | 1.0212 /
1.0217 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B1 = forward | 2.645 / 2.661
| 2.578 / 2.595 | 1.0260 / 1.0254 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.733 / 9.759 | 9.605 / 9.625 | 1.0133 / 1.0139 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.848 / 2.867 | 2.740 / 2.774 | 1.0394 / 1.0335 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.391 / 10.428 | 10.190 /
10.213 | 1.0197 / 1.0211 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.533 /
2.550 | 2.478 / 2.481 | 1.0222 / 1.0278 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.086 / 9.097 | 8.969 / 8.980 | 1.0130 /
1.0130 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B1 = forward | 2.476 / 2.498
| 2.412 / 2.429 | 1.0265 / 1.0284 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 8.991 / 9.006 | 8.862 / 8.889 | 1.0146 / 1.0132 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.602 / 2.579 | 2.524 / 2.491 | 1.0309 / 1.0353 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 9.546 / 9.516 | 9.397 / 9.361 |
1.0159 / 1.0166 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B1 = forward | 2.800 /
2.832 | 2.740 / 2.766 | 1.0219 / 1.0239 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.254 / 10.272 | 10.113 / 10.146 |
1.0139 / 1.0124 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B1 = forward | 2.871 / 2.771
| 2.692 / 2.699 | 1.0665 / 1.0267 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 10.139 / 10.162 | 10.244 / 10.034 | 0.9898 / 1.0128
|
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 3.034 / 3.060 | 2.909 / 2.924 | 1.0430 / 1.0465 |
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 11.167 / 11.201 | 10.932 /
10.946 | 1.0215 / 1.0233 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B1 = forward | 2.670 /
2.661 | 2.513 / 2.520 | 1.0625 / 1.0560 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.534 / 9.561 | 9.327 / 9.345 | 1.0222 /
1.0231 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B1 = forward | 2.592 / 2.615
| 2.530 / 2.543 | 1.0245 / 1.0283 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.496 / 9.519 | 9.486 / 9.385 | 1.0011 / 1.0143 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.862 / 2.772 | 2.672 / 2.659 | 1.0711 / 1.0425 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.150 / 10.116 | 9.919 / 9.899
| 1.0233 / 1.0219 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B1 = forward | 2.756 /
2.797 | 2.695 / 2.728 | 1.0226 / 1.0253 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.050 / 10.081 | 9.913 / 9.942 | 1.0138
/ 1.0140 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B1 = forward | 2.687 / 2.713
| 2.622 / 2.640 | 1.0248 / 1.0277 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.926 / 9.958 | 9.802 / 9.805 | 1.0127 / 1.0156 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.978 / 2.983 | 2.851 / 2.848 | 1.0445 / 1.0474 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.848 / 10.890 | 10.615 /
10.655 | 1.0220 / 1.0221 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.700 /
2.725 | 2.639 / 2.649 | 1.0231 / 1.0287 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.800 / 9.813 | 9.667 / 9.704 | 1.0138 /
1.0112 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B1 = forward | 2.649 / 2.679
| 2.577 / 2.599 | 1.0279 / 1.0308 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.727 / 9.769 | 9.600 / 9.620 | 1.0132 / 1.0155 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.777 / 2.782 | 2.798 / 2.680 | 0.9925 / 1.0381 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.315 / 10.329 | 10.112 /
10.137 | 1.0201 / 1.0189 |

The family's other Cake variants, neither changed by this PR, are the
single-device packed training variant (forward + backward in
saved-context and checkpoint-replay modes) and the halo variant of the
width-4 causal conv1d + SiLU training backend that ships beside the
context-parallel variant; the family covers sm_100a (B200 / GB200),
sm_103a (B300 / GB300) and sm_107a (R200), the new transfer program is
built for all three, and the table measures GB300.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* The default transfer method for experimental KDA training now uses the
half-width BF16x3 walk. The TF32 hi/lo walk remains available through
explicit test selection.
* Added prebuilt KDA training libraries for additional GPU
architectures.
* **Bug Fixes**
* KDA training now rejects a head count below one with a clear
validation error.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [316faec](https://github.com/flashinfer-ai/flashinfer/commit/316faec37a4706a2ecc7d46265087f8190b40baa)

- **作者**: Yang Xu
- **时间**: 2026-10-24T18:58:22Z
- **提交信息**: perf(moe): extend bounded SM120 BF16 TC decode through eight tokens (#7190)

<!-- .github/pull_request_template.md -->

## 📌 Description

The native SM12x BF16/NVFP4 decode path stops using direct routing with
fused Tensor Core sum above four tokens. For small experts this falls
back to expensive route packing at T7/8. Extend the existing path
through T8 only on SM120 with packed NVFP4/E4M3 block-16 scales,
H<=2048, I<=512 and top-k<=10. Existing activation, expert-map, route
and amax guards remain; runtime-compiled and preplanned calls share the
bound. Larger shapes and SM121 retain the old cap, and FP16 behavior is
unchanged.

On RTX PRO 6000 Blackwell Workstation Edition, H2048/I512/E512/K10/T8,
SwiGLU:

| Routes / cache | Original native µs | Improved native µs | Speedup |
|---|---:|---:|---:|
| Shared / warm | 93.807 | 39.840 | 2.355× |
| Shared / cold | 107.423 | 48.848 | 2.199× |
| Disjoint / warm | 163.919 | 63.808 | 2.569× |
| Disjoint / cold | 195.935 | 103.615 | 1.891× |

Each version independently tunes the native tile pairs plus default,
then runs native/Frost ABBA validation. The cross-version comparison
uses separate processes with unchanged Frost as a control (<=0.1% median
drift); it is not a direct two-version ABBA run. CUPTI measures complete
routed-expert GPU calls, excluding weight preparation, routing-network
evaluation, shared experts, EP communication and host enqueue. These are
not model throughput results.

The stronger native baseline reduces the prior T8/shared Frost advantage
from about2.6× to1.11× warm and parity cold. Docs and compact
measurement records retain that correction, all native candidate
medians, correctness and A/A controls, source/software identity, and
reproduction commands. CUDA13.0, PyTorch2.14.1+cu130, CuTeDSL4.8.0,
tvm-ffi0.1.14.post1.

Unrestricted TC decode regressed H7168/I2048 shared experts
substantially in a separate diagnostic cohort; those shapes remain
excluded. T5/T6 and smaller-shape diagnostics retain gains. This is a
bounded policy for the existing MMA implementation, not a replacement
kernel.

## 🔍 Related Issues

Follow-up to #7186. Related Frost coverage work: #7189; this PR is
independent of that change.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All targeted local tests are passing. Normal CI/review remains
separate.

- New T5/6/7/8 live-route/graph tests plus existing FP16
regression:30passed.
- Targeted route-pack, compile-cache and unified
integration:171passed,35deselected.
- Independent FP64-dot references; changed inputs/routes, invalid IDs
with NaN scores, poisoned outputs, and no route-pack fallback for
preplanned/runtime compilation.
- Scoped `pre-commit run --files ...` and `git diff --check` passed. The
all-files checkbox remains unchecked because unrelated files were not
reformatted.
- Ordinary merge with current main preserved all measured
runtime/test/benchmark hashes.

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

Please check the shape/architecture admission, preplanned-launch guard,
and numerical distinction: the existing fused TC epilogue uses BF16
atomic accumulation, while the original path combines FP32 expert
partials. Both pass the independent reference
at1%relativeL2/3%normalizedmax; they are not bitwise-equivalent rounding
contracts. No new numerical knob is introduced.

Details and reproducible commands: `docs/sm120_w4a16_decode.md`. The
change does not add a default Frost selection or publish SM107
performance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* On supported SM120 hardware, BF16/NVFP4 workloads can use Tensor Core
decoding for up to eight tokens when the input dimensions and formats
meet the supported limits. Other configurations retain the existing
four-token limit; FP16 behavior is unchanged.

* **Documentation**
* Added guidance on supported configurations, performance comparisons,
accuracy, and benchmark methodology.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a9e02c2](https://github.com/flashinfer-ai/flashinfer/commit/a9e02c23923b724293c583961915b438cece32eb)

- **作者**: Yang Xu
- **时间**: 2026-10-24T18:41:58Z
- **提交信息**: feat(moe): add Frost PowLU and SM120 W8 route reuse (#7189)

<!-- .github/pull_request_template.md -->

## 📌 Description

Frost currently rejects `PowLU`, and its E4M3 weight-only FC1 reloads
weights independently for repeated expert routes. This batch adds
`PowLU(m, limit)` to the shared scalar/vector epilogues and reuses the
existing FP4 route-group implementation for BF16/FP16-input E4M3
weights. Only SM120 T>=4 advertises the 24 additional grouped choices,
alongside all 16 original choices. Default backend/tactic selection is
unchanged.

The PowLU implementation preserves positive subnormals, handles positive
infinity, and applies the public exponent/clamp contract. Weight-only
FC1 grouping keeps independent typed accumulators and live routing; FC2
and ordered combine are unchanged. No new backend or public signature is
introduced.

Kernel GPU-call measurements below use H=2048, I=512, E=512, top-k=10.
W8 incremental rows compare the best original 16 Frost tactics with the
expanded 40, on the same checkpoint and numerical contract. The separate
cuTile cohort searches 337 native choices. These cohorts use different
deterministic checkpoint generators; their speedups cannot be
multiplied.

| BF16 W8, shared experts | Warm baseline → Frost µs | Speedup | Cold
baseline → Frost µs | Speedup |
|---|---:|---:|---:|---:|
| SM120 T4, original Frost | 22.160 → 19.792 | 1.120× | 33.480 → 33.648
| 0.995× |
| SM120 T8, original Frost | 38.864 → 36.031 | 1.079× | 52.927 → 51.872
| 1.020× |
| SM120 T4, cuTile | 25.503 → 19.127 | 1.333× | 39.976 → 33.264 | 1.202×
|
| SM120 T8, cuTile | 28.800 → 35.199 | 0.818× | 43.104 → 51.344 | 0.840×
|

SM120 is RTX PRO 6000 Blackwell Workstation Edition. FP16-input W8 shows
similar incremental gains; disjoint routes are effectively unchanged. T2
was excluded after its 7–8% cold regression. cuTile remains faster at T8
despite the incremental Frost gain.

For BF16 `PowLU()` with disjoint routes, the baseline is CUTLASS's
per-stage tuning followed by its top-two-by-top-two compound pairs and
default:

| GPU / T | Warm CUTLASS → Frost µs | Speedup | Cold CUTLASS → Frost µs
| Speedup |
|---|---:|---:|---:|---:|
| H100 / 1 | 52.648 → 25.500 | 2.065× | 58.640 → 32.704 | 1.793× |
| H100 / 8 | 170.532 → 142.504 | 1.197× | 178.608 → 151.828 | 1.176× |
| B200 / 1 | 44.292 → 12.064 | 3.671× | 51.636 → 19.880 | 2.597× |
| B300 / 1 | 38.840 → 14.748 | 2.634× | 52.392 → 26.228 | 1.998× |
| B300 / 8 | 161.608 → 143.004 | 1.130× | 170.176 → 153.292 | 1.110× |

All 24 PowLU cases, 16 W8 incremental cases and four native-boundary
cases are retained in `benchmarks/data/`, with source/software identity,
frozen tactics, reference errors and A/A controls. Reproduction commands
and the full tables are in `docs/frost_low_latency_moe.md`.

The four additional PowLU cases use H=7168, I=2048, E=256, top-k=8, T=1:
H100 improves 1.137× warm / 1.129× cold, and B300 improves 1.063× /
1.051×. These larger cases show the narrower advantage as weight traffic
grows.

These are complete routed-expert GPU-call intervals, including backend
adapters and combine, excluding host enqueue, weight preparation,
routing selection, shared experts, EP communication and serving
throughput. W8 uses CUPTI plus separate warm event controls; PowLU uses
CUDA events on H100 and globaltimer intervals on B200/B300. Globaltimer
empty-boundary overhead is recorded without subtraction. PowLU
cross-backend checks are tolerance-based, not bitwise equivalence.

## 🔍 Related Issues

Builds on #7186 and the existing Frost weight-only pipeline.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All targeted local tests are passing (`unittest`, etc.). CI
remains a separate check.

- Combined W8/PowLU suite on SM120: **671 passed, 1 skipped**.
- Expanded PowLU parameter/format matrix, including m<1, clamp, T4/T8,
scalar/vector boundaries and graph updates: **H100 120 passed / 12
architecture skips; B200, B300 and SM120 132 passed each**.
- Earlier standalone W8 suite: 370 passed / 4 skipped; mixed-output
partial-group checks: 36 passed; architecture/token/dtype admission: 32
passed.
- B300 full PowLU regression: 529 passed. B200 host binding,
concurrent-stream and storage-lifetime suite: **77 passed**.
- Scoped `pre-commit run --files ...` and `git diff --check` passed. The
all-files checkbox is intentionally left unchecked; unrelated files were
not reformatted.

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

Please check route-group ownership/predication, the E4M3 versus FP4
scale layout, typed rounding, and PowLU parameter lowering. Graph tests
change route IDs, inputs and scales and cover mixed output types,
partial groups, invalid routes and fresh bindings.

The new grouping is not advertised for quantized FP8 activations or
non-SM120 architectures. SM107 performance is not part of this report.
Native SM107 qualification for this batch remains with current-head
CI/review; dependency-based skips are not device coverage.

The compact JSON records preserve all represented numeric values. PowLU
retains compared-path samples and A/A/reference controls; W8 records
retain candidate/validation medians and controls rather than every
individual CUPTI sample. The separate native BF16 T8 prototype and PowLU
fast-math experiments are not in this PR.

### [f5d4db2](https://github.com/flashinfer-ai/flashinfer/commit/f5d4db2c488d77331afa653c282d2e03c87ba517)

- **作者**: Yang Xu
- **时间**: 2026-10-24T16:51:33Z
- **提交信息**: feat(moe): extend Frost weight-only decode to FP16 (#7186)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend Frost weight-only NVFP4, MXFP4, MXINT4 and E4M3 to FP16
inputs/intermediates and independently selected BF16/FP16 outputs. Reuse
the existing two-kernel FMA pipeline, typed activations, preparation and
ordered combine. Quantized-activation FP8 keeps its previous contract.

Expose qualified FP16 wide-load choices and Hopper FC1 route groups.
Also improve the native SM120 FP16/NVFP4 comparator: direct routing
through T=8 is bounded to H<=2048, I<=512, top-k<=10; larger experts
retain their existing packing policy. The default Frost backend list is
unchanged.

Complete routed-expert GPU time, SwiGLU H2048/I512/E512/K10. Warm/cold
are separate measurements, not model throughput:

| GPU / FP16 input, weight format | Comparator | Warm baseline -> Frost
(us) | Cold baseline -> Frost (us) |
|---|---|---:|---:|
| H100 / NVFP4 / T1 | Exact expanded FP16 CUTLASS | 54.024 -> 15.776
(3.424x) | 61.296 -> 19.216 (3.190x) |
| H100 / E4M3 / T8, shared experts | Exact expanded FP16 CUTLASS |
51.896 -> 46.504 (1.116x) | 59.216 -> 55.568 (1.066x) |
| H100 / MXFP4 / T8, shared experts | Exact expanded FP16 CUTLASS |
51.928 -> 78.040 (0.665x) | 58.911 -> 85.408 (0.690x) |
| SM120 / NVFP4 / T1 | Tuned native FP16 TC | 11.104 -> 7.776 (1.428x) |
21.000 -> 19.488 (1.078x) |
| SM120 / NVFP4 / T8, shared experts | Improved native FP16 TC in this
PR | 40.032 -> 34.504 (1.160x) | 49.064 -> 50.288 (0.976x) |

Expanded controls require 4x FP4/INT4 or 2x E4M3 weight payload storage
and exclude expansion time. They are not native low-bit baselines. Each
path is validated against its own rounding contract; native SM120 keeps
FP32 preactivation/expert partials, while these Frost cases round them
to FP16. Cold cases can lose. Reproducer, source fingerprints, full
measurements and numerical boundaries are in
`benchmarks/bench_frost_low_latency_w4a16.py`,
`benchmarks/data/frost_weight_only_fp16_20261024.json` and
`docs/frost_low_latency_moe.md`.

## 🔍 Related Issues

Follows #7184 and reuses the existing Frost low-latency implementation.
Includes the earlier MXFP4 benchmark architecture-preflight suggestion
from that review.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted tests pass on the tested devices; capability skips are
reported separately.

Full FP16 coverage suites: H100 470 passed / 17 skipped, B300 480 / 7,
SM120 466 / 21. Follow-up qualification covers Hopper grouped tactics
(186 passed), native SM120 routing plus related regressions (134
passed), and the final combined SM120 suite (201 passed). Tests include
all typed activations, raw/final outputs, independent FP64-dot
references, changed graph routing/scales/inputs and dtype cache
separation. SM107 FP16 weight-only device qualification remains pending;
no SM107 timing claims are included.

Scoped pre-commit checks pass for all 17 changed files. The review
cleanup also reran all four affected wide-load graph cases successfully
on B300. The template all-files box is left unchecked because unrelated
files were not reformatted.

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

Please focus on input/output dtype separation and rounding boundaries,
group ownership under changed routes, and the native direct-routing
envelope. A blanket T8 extension was rejected because large shared
experts regress severely. The bounded native improvement prevents the
Frost comparison from relying on that weak baseline. Kernel
implementation is AI-assisted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Frost low-latency MoE now supports FP16 activations with NVFP4, MXFP4,
MXINT4, and per-tensor FP8 weight-only execution, alongside existing
BF16 support.
* Supported weight-only configurations can select FP16 or BF16 output
independently of activation format.
* FP16 routing and execution support is expanded for eligible GPU
architectures and input shapes.
* **Benchmarks**
* The low-latency benchmark now covers FP16 activations and
expanded-weight comparisons for supported formats and hardware.
* **Documentation**
* Updated supported configurations, dtype behavior, performance results,
and reproduction guidance.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d9f12de](https://github.com/flashinfer-ai/flashinfer/commit/d9f12dee0f1b1fb900343ff506c5c9ac566684b6)

- **作者**: Yang Xu
- **时间**: 2026-10-24T15:53:03Z
- **提交信息**: docs(prefill): refresh the Blackwell ragged d192/128 auto-order note with cuDNN 9.27 data (#7154)

<!-- .github/pull_request_template.md -->

## 📌 Description

Comment-only change in `flashinfer/prefill.py`. No behavior change: the
Blackwell ragged-prefill `auto` order and the empty per-head-dim table
stay as they are.

The note above `_BLACKWELL_RAGGED_AUTO_PREFERENCE_BY_HEAD_DIM` recorded
the d192/128 split measured with cuDNN 9.26: CUTLASS ahead at
long-sequence MHA, cuDNN ahead elsewhere. The header line just above it
also still read "d192/128 MHA ... -> CUTLASS first", which contradicts
the `("cudnn", "cutlass")` order it annotates.

The cell was re-measured on a full B200 (1000 W, 148 SMs) with
FlashInfer main `fa6994348` and cudnn-frontend 1.32. Only the cuDNN
library changed between columns: 9.26.0.51, 9.27.0.42 and 9.29 dev. The
method was `benchmarks/flashinfer_benchmark.py --routine
BatchPrefillWithRaggedKVCacheWrapper --backends cutlass cudnn
trtllm-native`, bf16, causal, 30 iterations after 10 warm-up, median of
two rounds with the library order reversed. Round-to-round spread was
under 2 %, and the first round ran with `--refcheck`.

- **cuDNN ≥ 9.27 leads all 15 d192/128 shapes measured, by 1.07-1.73x.**
These are the ten d192/128 shapes from #5133 plus five long-KV prefill
shapes. With 9.26, CUTLASS still led five long-sequence shapes, up to
1.28x.
- **The 9.26 loss was a cuDNN backend regression on the ragged/THD
d192/128 path**, tracked in NVIDIA/cudnn-frontend#1085 and fixed in
9.27.0. 9.29 dev matches 9.27.
- **The note now carries the measured table and says the default order
stands.** It also says that on 9.26, callers with long-sequence MHA can
pin `cutlass,cudnn` through `FLASHINFER_RAGGED_AUTO_BACKEND_ORDER`.

Not changed: the order itself. A cuDNN-version gate was considered and
rejected, because 9.26 still leads the short-sequence and GQA shapes by
1.6-1.7x.

## 🔍 Related Issues

Follows up #5133. NVIDIA/cudnn-frontend#1085.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on the changed file.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (Comment-only change;
nothing to test.)
- [ ] All tests are passing (`unittest`, etc.).

<sub>note to self: claude::973dbc96-41cf-4181-939f-5eff6faf3b58 — "Frost
engine性能对比与优化策略" · cwd /home/scratch.yanxu_libs/cudnn_frontend ·
workspace /home/scratch.yanxu_gpu/frost_default_bench (b200_fi/,
results/b200_fi/fi.log)</sub>

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Updated backend performance guidance with B200 benchmark results
across cuDNN 9.26, 9.27, and 9.29. cuDNN 9.27 leads on all measured
d192/128 shapes; earlier long-sequence results reflected a cuDNN
regression.
* Callers using cuDNN 9.26 can select CUTLASS before cuDNN. The default
backend preference remains unchanged.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [92ec5f0](https://github.com/flashinfer-ai/flashinfer/commit/92ec5f0976d0340be067d9ccbbbcd376756eead6)

- **作者**: Yang Xu
- **时间**: 2026-10-24T15:10:13Z
- **提交信息**: feat(moe): extend Frost low-latency to four-bit weight-only formats (#7184)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add explicit `frost_low_latency` support for NVFP4, MXFP4 and signed
MXINT4
weights with BF16 activations, preserving canonical checkpoint payloads
and
scales. All three formats share the existing two FMA kernels, ten typed
activations, precomputed routing, ordered combine and runtime binding
cache.
Support includes packed/unpacked routing and raw/final outputs at T≤8,
top-k≤32, H divisible by 128 and logical I divisible by 32.

The same batch adds independently tunable four/eight-value loads, an
exact
packed software FP4 decoder for Hopper, and dynamic FC1 expert-weight
reuse
across two/four route slots on Hopper. These use existing backend/config
selection; callers explicitly opt in and autotune. Default automatic
backend
selection is unchanged.

Complete routed-expert GPU intervals, H2048/I512/E512/K10/T1/SwiGLU:

| GPU / weights | Native | Warm native → Frost µs | Speedup | Cold
native → Frost µs | Speedup |
|---|---|---:|---:|---:|---:|
| H100 / NVFP4 | Exact offline BF16 expansion + CUTLASS | 49.840 →
16.128 | 3.090× | 57.440 → 19.600 | 2.931× |
| H100 / MXFP4 | CUTLASS | 43.216 → 16.928 | 2.553× | 51.655 → 20.104 |
2.569× |
| B300 / NVFP4 | CuTe DSL | 20.120 → 15.392 | 1.307× | 25.208 → 18.176 |
1.387× |
| B300 / MXFP4 | Prims-TS | 83.360 → 17.728 | 4.702× | 86.624 → 21.360 |
4.055× |
| B300 / MXINT4 | TRT-LLM | 22.688 → 18.272 | 1.242× | 25.568 → 22.496 |
1.137× |
| RTX PRO 6000 Blackwell / NVFP4 | SM12x warm; fused TC cold | 9.568 →
8.256 | 1.159× | 20.024 → 19.632 | 1.020× |
| RTX PRO 6000 Blackwell / MXFP4 | cuTile | 21.679 → 8.576 | 2.528× |
35.447 → 18.912 | 1.874× |

The H100 NVFP4 expanded control reconstructs identical quantized weights
before
timing and uses **4× packed-weight storage**. It is a stronger measured
control
than native cuTile, whose larger ratios are not used as the headline.
The B300
warm NVFP4 row revalidates a faster prior native tile instead of
accepting the
short search winner. All other rows retain native packed four-bit
execution.

The near-parity SM120 NVFP4 cold result is intentional. The benchmark
audits
multiple applicable native implementations instead of assuming one is
best.
H100 MXFP4 T8/shared remains slower: 45.056→78.528µs (0.574×).
B300 MXINT4 H4096/I1536/E128/K8/T1 also loses: 58.688→77.040µs warm
(0.762×), 60.720→82.832µs cold (0.733×).

Each pair uses the same GPU, checkpoint, routes, shape and cache
condition.
Candidate search precedes frozen ABBA validation. CUPTI measures the
first-to-last
GPU activity span with independent warm CUDA-event controls on
H100/SM120;
B300 uses graph globaltimer with empty-interval and A/A controls,
without an
independent CUDA-event control. Weight preparation, routing-network
evaluation, shared experts,
communication, host submission and serving are outside the interval.
Synthetic
model-shaped kernel tests are not model-throughput measurements.

Frost FP4 rounds preactivation/intermediate/expert values to BF16;
MXINT4 keeps
FP32 preactivation. Some native Blackwell paths keep FP32 preactivation
or
expert partials, and SM12x uses FP16 partial dot products. Independent
references
cover each numerical contract; these are not universally
bitwise-equivalent
rounding paths. The reproducer also includes an exact expanded-BF16
control
for NVFP4, with its larger weight storage explicitly identified.

Reproduce with `benchmarks/bench_frost_low_latency_w4a16.py`; the
updated guide
and compact cumulative record include configuration, absolute times,
validation
and losing boundaries. No serving speedup is claimed.

## 🔍 Related Issues

Builds on the merged Frost low-latency infrastructure and #7153, #7162,
#7166 and #7174.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted GPU tests pass; required CI will be requested on the
final head.

Final main-integrated twelve-file suite: H100 402 passed / 17 skipped;
B300 412 passed / 7 skipped; SM120 398 passed / 21 skipped. Skips are
explicit
architecture-specific lanes, not counted as device execution. Fresh
SM100/SM107
qualification remains for CI.

Coverage includes exhaustive packed-word decoding, scale ranges, all
typed
activations, tail dimensions, max routes/tokens, invalid IDs with
nonfinite
scores, raw/final routing contracts, changed-input graph replay, fresh
tensor
bindings on warm metadata, and all advertised Hopper T1/T2 tactics.
Scoped
pre-commit hooks are used instead of reformatting unrelated files.

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

Review group ownership/masking, canonical checkpoint preservation,
scale-range
handling and runtime dtype/pointer validation. The signed INT4
conversion is
adapted from the existing TRT-LLM/CUTLASS numeric converter and
acknowledged in
source. The Hopper E2M1 lookup is exhaustively checked including
negative zero.

SM103/SM120 expose 64 width/column choices. Hopper NVFP4/MXFP4 exposes
64 for
T1 and 88 including route groups for T≥2. SM100/SM107 and Hopper MXINT4
retain
16 column pairs pending wider-load performance qualification. Low token
count
alone does not imply a win; the guide retains larger/shared-expert
losses.

FP16 weight-only activation work is a separate follow-up; it is not part
of
this PR. No Tensor Core kernel or monokernel is introduced here.

Review follow-up: allocate independent FC1/FC2 unit scales for non-gated
MXFP4/MXINT4. The strengthened live-scale graph tests reproduce ten
failures before the fix; the post-fix three-file B300 suite passes 117
tests. The GPU kernel sources and measured cumulative performance
records are unchanged. The stored runtime fingerprint intentionally
identifies the measured version.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added Frost Low Latency support for NVFP4, MXFP4, and MXINT4
weight-only workloads with BF16 activations on supported GPUs.
* Added weight-preparation options for all three formats, with
validation for supported inputs and scales.
* Added route-grouping and wider-load tactic options for eligible
workloads.
* **Documentation**
* Expanded format and architecture guidance, including supported
constraints and benchmark results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9a575dd](https://github.com/flashinfer-ai/flashinfer/commit/9a575dd5d8c9fa461bb5affa14dd03a2ab9545fa)

- **作者**: eigen
- **时间**: 2026-10-24T14:05:16Z
- **提交信息**: feat(cake_vsa_sm90): add grouped-query (GQA) variant of the variable block-sparse attention forward (#7167)

FlashInfer's Cake backend for variable block-sparse attention on Hopper
(`VariableBlockSparseAttentionWrapper(backend="cake")`, sm_90a) supports
two data types: BF16 and Sage-FP8 (E4M3 inputs with per-head scales,
BF16 output). Each data type has persistent programs for long rows and
small-selection programs for short rows. Before this PR, every program
was multi-head (MHA), so grouped-query attention ran on the MHA kernels
after K, V, the scales and the block mask were repeated g times to
num_qo_heads. This PR adds the grouped-query (GQA) variant for both data
types, for g ∈ {2, 4, 8} including MQA. It ships 40 GQA programs and
planner routing that selects them when num_qo_heads exceeds
num_kv_heads. The g query heads of each KV head share that head's K/V
stream and sparse pattern, with FP8 q_scale per query head and
k_scale/v_scale per KV head, which brings the family to 80 programs with
the MHA programs and public API names unchanged. The baseline is the
previous Cake version serving GQA by K/V replication, with replication
not timed. Against it, the geometric-mean speedup over the 284 shapes
below (142 shapes × BF16 and E4M3, g = 4 on 83 shapes and g = 8 on 59)
is 1.186× (range 1.005× to 2.304×): 1.239× for BF16 (g4 1.219×, g8
1.267×) and 1.135× for E4M3 (g4 1.125×, g8 1.150×). Times are kernel
time per forward in microseconds on an H100 80GB, and shapes are named
hH-mM-nN-kK-raggedR-scaleS-gG (H query heads, M query tokens, N KV
tokens, K selected 64-token KV blocks per query block, ragged = variable
K per query block, scale = softmax scale variant, g = query heads per KV
head).

Grouped-query variable block-sparse attention forward, NVIDIA H100 80GB
HBM3 (sm_90a), CUDA 13.4 toolkit (JIT-compiled; torch 2.14.1+cu130),
driver 535.216.03: previous Cake version (the MHA kernels serving GQA by
K/V replication) vs this version (native GQA kernels), absolute kernel
time per forward in microseconds (CUPTI kernel-sum, cold L2, 9 groups x
256 iterations, two interleaving orders, process a of the two-process
acceptance run; speedup = previous / this).

| shape | dtype | previous µs | this µs | speedup |
|---|---|---|---|---|
| h4-m256-n256-k1-ragged0-scale0-g4 | bf16 | 3.168 | 3.072 | 1.031x |
| h4-m256-n256-k1-ragged0-scale0-g4 | e4m3 | 3.040 | 2.944 | 1.033x |
| h8-m256-n256-k3-ragged0-scale0-g4 | bf16 | 5.152 | 4.736 | 1.088x |
| h8-m256-n256-k3-ragged0-scale0-g4 | e4m3 | 4.704 | 4.352 | 1.081x |
| h8-m1024-n1024-k4-ragged0-scale0-g4 | bf16 | 7.392 | 6.496 | 1.138x |
| h8-m1024-n1024-k4-ragged0-scale0-g4 | e4m3 | 6.464 | 5.664 | 1.141x |
| h8-m1024-n1024-k12-ragged0-scale0-g4 | bf16 | 10.911 | 10.336 | 1.056x
|
| h8-m1024-n1024-k12-ragged0-scale0-g4 | e4m3 | 10.400 | 10.048 | 1.035x
|
| h8-m2048-n2048-k8-ragged0-scale0-g4 | bf16 | 14.336 | 12.800 | 1.120x
|
| h8-m2048-n2048-k8-ragged0-scale0-g4 | e4m3 | 13.535 | 11.456 | 1.181x
|
| h8-m2048-n2048-k16-ragged0-scale0-g4 | bf16 | 21.344 | 20.256 | 1.054x
|
| h8-m2048-n2048-k16-ragged0-scale0-g4 | e4m3 | 20.032 | 18.624 | 1.076x
|
| h8-m4096-n4096-k16-ragged0-scale0-g4 | bf16 | 37.152 | 33.471 | 1.110x
|
| h8-m4096-n4096-k16-ragged0-scale0-g4 | e4m3 | 35.583 | 32.032 | 1.111x
|
| h8-m4096-n4096-k32-ragged0-scale0-g4 | bf16 | 61.024 | 57.760 | 1.057x
|
| h8-m4096-n4096-k32-ragged0-scale0-g4 | e4m3 | 58.975 | 55.968 | 1.054x
|
| h4-m512-n1024-k4-ragged0-scale0-g4 | bf16 | 5.792 | 5.152 | 1.124x |
| h4-m512-n1024-k4-ragged0-scale0-g4 | e4m3 | 5.248 | 4.832 | 1.086x |
| h4-m1024-n512-k4-ragged1-scale0-g4 | bf16 | 5.760 | 5.376 | 1.071x |
| h4-m1024-n512-k4-ragged1-scale0-g4 | e4m3 | 5.120 | 4.801 | 1.066x |
| h4-m1024-n1024-k8-ragged1-scale0-g4 | bf16 | 6.752 | 6.144 | 1.099x |
| h4-m1024-n1024-k8-ragged1-scale0-g4 | e4m3 | 5.921 | 5.568 | 1.063x |
| h4-m512-n512-k4-ragged0-scale1-g4 | bf16 | 5.504 | 5.056 | 1.089x |
| h4-m512-n512-k4-ragged0-scale1-g4 | e4m3 | 5.088 | 4.736 | 1.074x |
| h16-m1024-n8192-k1-ragged0-scale0-g4 | bf16 | 9.504 | 6.720 | 1.414x |
| h16-m1024-n8192-k1-ragged0-scale0-g4 | e4m3 | 6.560 | 5.345 | 1.227x |
| h8-m512-n4096-k2-ragged0-scale0-g4 | bf16 | 5.856 | 4.928 | 1.188x |
| h8-m512-n4096-k2-ragged0-scale0-g4 | e4m3 | 4.960 | 4.256 | 1.165x |
| h4-m2048-n4096-k6-ragged0-scale0-g4 | bf16 | 9.248 | 7.839 | 1.180x |
| h4-m2048-n4096-k6-ragged0-scale0-g4 | e4m3 | 7.776 | 7.136 | 1.090x |
| h4-m2048-n4096-k6-ragged0-scale0-uneven-g4 | bf16 | 8.752 | 7.392 |
1.184x |
| h4-m2048-n4096-k6-ragged0-scale0-uneven-g4 | e4m3 | 7.232 | 6.528 |
1.108x |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g4 | bf16 | 24.768 | 22.656 |
1.093x |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g4 | e4m3 | 22.593 | 22.209 |
1.017x |
| h32-m2048-n2048-k8-ragged0-scale0-g4 | bf16 | 42.527 | 38.624 | 1.101x
|
| h32-m2048-n2048-k8-ragged0-scale0-g4 | e4m3 | 40.352 | 37.280 | 1.082x
|
| h16-m4096-n16384-k16-ragged0-scale0-g4 | bf16 | 85.375 | 59.488 |
1.435x |
| h16-m4096-n16384-k16-ragged0-scale0-g4 | e4m3 | 70.400 | 57.024 |
1.235x |
| h8-m1024-n32768-k64-ragged0-scale0-g4 | bf16 | 55.967 | 36.128 |
1.549x |
| h8-m1024-n32768-k64-ragged0-scale0-g4 | e4m3 | 34.528 | 32.288 |
1.069x |
| h8-m2048-n32768-k48-ragged1-scale0-g4 | bf16 | 55.344 | 31.424 |
1.761x |
| h8-m2048-n32768-k48-ragged1-scale0-g4 | e4m3 | 40.895 | 28.577 |
1.431x |
| h32-m8192-n8192-k24-ragged0-scale0-g4 | bf16 | 380.525 | 340.526 |
1.117x |
| h32-m8192-n8192-k24-ragged0-scale0-g4 | e4m3 | 337.151 | 310.256 |
1.087x |
| h16-m8192-n8192-k5-ragged0-scale0-g4 | bf16 | 61.920 | 52.384 | 1.182x
|
| h16-m8192-n8192-k5-ragged0-scale0-g4 | e4m3 | 54.656 | 51.264 | 1.066x
|
| h8-m8192-n8192-k2-ragged0-scale0-g4 | bf16 | 27.904 | 20.288 | 1.375x
|
| h8-m8192-n8192-k2-ragged0-scale0-g4 | e4m3 | 22.112 | 16.256 | 1.360x
|
| h8-m4096-n4096-k64-ragged0-scale1-g4 | bf16 | 107.248 | 106.751 |
1.005x |
| h8-m4096-n4096-k64-ragged0-scale1-g4 | e4m3 | 101.519 | 100.768 |
1.007x |
| h8-m4096-n4096-k20-ragged1-scale0-g4 | bf16 | 29.648 | 25.824 | 1.148x
|
| h8-m4096-n4096-k20-ragged1-scale0-g4 | e4m3 | 27.360 | 24.576 | 1.113x
|
| h8-m512-n512-k1-ragged0-scale0-g4 | bf16 | 4.160 | 3.616 | 1.150x |
| h8-m512-n512-k1-ragged0-scale0-g4 | e4m3 | 3.488 | 3.232 | 1.079x |
| h8-m512-n1024-k2-ragged0-scale0-g4 | bf16 | 5.376 | 4.800 | 1.120x |
| h8-m512-n1024-k2-ragged0-scale0-g4 | e4m3 | 4.736 | 4.128 | 1.147x |
| h16-m256-n512-k2-ragged1-scale0-g4 | bf16 | 5.280 | 4.640 | 1.138x |
| h16-m256-n512-k2-ragged1-scale0-g4 | e4m3 | 4.609 | 4.000 | 1.152x |
| h8-m1024-n2048-k4-ragged0-scale0-g4 | bf16 | 8.128 | 6.592 | 1.233x |
| h8-m1024-n2048-k4-ragged0-scale0-g4 | e4m3 | 6.880 | 5.728 | 1.201x |
| h8-m1024-n4096-k6-ragged0-scale0-g4 | bf16 | 11.488 | 7.904 | 1.453x |
| h8-m1024-n4096-k6-ragged0-scale0-g4 | e4m3 | 8.192 | 7.264 | 1.128x |
| h4-m2048-n2048-k5-ragged0-scale0-g4 | bf16 | 8.096 | 7.296 | 1.110x |
| h4-m2048-n2048-k5-ragged0-scale0-g4 | e4m3 | 7.104 | 6.560 | 1.083x |
| h8-m256-n4096-k8-ragged0-scale0-g4 | bf16 | 7.968 | 6.400 | 1.245x |
| h8-m256-n4096-k8-ragged0-scale0-g4 | e4m3 | 6.817 | 5.792 | 1.177x |
| h8-m256-n2048-k8-ragged0-scale0-g4 | bf16 | 7.520 | 6.304 | 1.193x |
| h8-m256-n2048-k8-ragged0-scale0-g4 | e4m3 | 6.784 | 5.696 | 1.191x |
| h4-m256-n2048-k7-ragged0-scale0-g4 | bf16 | 5.792 | 5.024 | 1.153x |
| h4-m256-n2048-k7-ragged0-scale0-g4 | e4m3 | 5.024 | 4.608 | 1.090x |
| h8-m512-n4096-k8-ragged0-scale0-g4 | bf16 | 10.144 | 7.136 | 1.422x |
| h8-m512-n4096-k8-ragged0-scale0-g4 | e4m3 | 8.192 | 6.336 | 1.293x |
| h16-m256-n2048-k7-ragged1-scale0-g4 | bf16 | 8.607 | 6.656 | 1.293x |
| h16-m256-n2048-k7-ragged1-scale0-g4 | e4m3 | 7.168 | 5.952 | 1.204x |
| h8-m256-n4096-k9-ragged0-scale0-g4 | bf16 | 8.224 | 6.464 | 1.272x |
| h8-m256-n4096-k9-ragged0-scale0-g4 | e4m3 | 6.720 | 5.824 | 1.154x |
| h4-m512-n2048-k9-ragged0-scale0-g4 | bf16 | 6.848 | 6.112 | 1.120x |
| h4-m512-n2048-k9-ragged0-scale0-g4 | e4m3 | 6.240 | 5.664 | 1.102x |
| h8-m512-n4096-k12-ragged0-scale0-g4 | bf16 | 11.855 | 8.000 | 1.482x |
| h8-m512-n4096-k12-ragged0-scale0-g4 | e4m3 | 8.512 | 7.456 | 1.142x |
| h8-m256-n2048-k10-ragged0-scale0-g4 | bf16 | 8.064 | 6.912 | 1.167x |
| h8-m256-n2048-k10-ragged0-scale0-g4 | e4m3 | 7.072 | 6.432 | 1.100x |
| h8-m256-n4096-k16-ragged0-scale0-g4 | bf16 | 12.256 | 9.632 | 1.272x |
| h8-m256-n4096-k16-ragged0-scale0-g4 | e4m3 | 9.248 | 8.544 | 1.082x |
| h4-m256-n4096-k14-ragged0-scale0-g4 | bf16 | 7.392 | 6.112 | 1.209x |
| h4-m256-n4096-k14-ragged0-scale0-g4 | e4m3 | 6.559 | 5.696 | 1.152x |
| h4-m256-n8192-k18-ragged0-scale0-g4 | bf16 | 9.568 | 7.552 | 1.267x |
| h4-m256-n8192-k18-ragged0-scale0-g4 | e4m3 | 7.712 | 7.040 | 1.095x |
| h8-m128-n4096-k17-ragged0-scale0-g4 | bf16 | 8.736 | 6.912 | 1.264x |
| h8-m128-n4096-k17-ragged0-scale0-g4 | e4m3 | 7.184 | 6.432 | 1.117x |
| h4-m256-n8192-k24-ragged0-scale0-g4 | bf16 | 11.200 | 8.959 | 1.250x |
| h4-m256-n8192-k24-ragged0-scale0-g4 | e4m3 | 8.992 | 8.256 | 1.089x |
| h8-m256-n16384-k32-ragged0-scale0-g4 | bf16 | 20.128 | 17.888 | 1.125x
|
| h8-m256-n16384-k32-ragged0-scale0-g4 | e4m3 | 17.984 | 17.248 | 1.043x
|
| h4-m512-n16384-k20-ragged0-scale0-g4 | bf16 | 15.040 | 10.336 | 1.455x
|
| h4-m512-n16384-k20-ragged0-scale0-g4 | e4m3 | 11.104 | 9.472 | 1.172x
|
| h8-m128-n32768-k64-ragged0-scale0-g4 | bf16 | 29.376 | 21.408 | 1.372x
|
| h8-m128-n32768-k64-ragged0-scale0-g4 | e4m3 | 21.185 | 18.016 | 1.176x
|
| h4-m256-n8192-k48-ragged0-scale0-g4 | bf16 | 16.256 | 12.448 | 1.306x
|
| h4-m256-n8192-k48-ragged0-scale0-g4 | e4m3 | 11.808 | 10.784 | 1.095x
|
| h8-m256-n4096-k12-ragged0-scale0-uneven-g4 | bf16 | 7.808 | 6.848 |
1.140x |
| h8-m256-n4096-k12-ragged0-scale0-uneven-g4 | e4m3 | 6.847 | 6.368 |
1.075x |
| h8-m512-n8192-k24-ragged0-scale0-uneven-g4 | bf16 | 14.655 | 10.400 |
1.409x |
| h8-m512-n8192-k24-ragged0-scale0-uneven-g4 | e4m3 | 10.656 | 9.152 |
1.164x |
| h8-m256-n4096-k8-ragged0-scale1-g4 | bf16 | 7.904 | 6.368 | 1.241x |
| h8-m256-n4096-k8-ragged0-scale1-g4 | e4m3 | 6.880 | 5.760 | 1.194x |
| h32-m2048-n2048-k8-ragged0-scale0-g4 | bf16 | 42.527 | 38.624 | 1.101x
|
| h32-m2048-n2048-k8-ragged0-scale0-g4 | e4m3 | 40.352 | 37.280 | 1.082x
|
| h16-m4096-n16384-k16-ragged0-scale0-g4 | bf16 | 85.375 | 59.488 |
1.435x |
| h16-m4096-n16384-k16-ragged0-scale0-g4 | e4m3 | 70.400 | 57.024 |
1.235x |
| h8-m1024-n32768-k64-ragged0-scale0-g4 | bf16 | 55.967 | 36.128 |
1.549x |
| h8-m1024-n32768-k64-ragged0-scale0-g4 | e4m3 | 34.528 | 32.288 |
1.069x |
| h8-m2048-n32768-k48-ragged1-scale0-g4 | bf16 | 55.344 | 31.424 |
1.761x |
| h8-m2048-n32768-k48-ragged1-scale0-g4 | e4m3 | 40.895 | 28.577 |
1.431x |
| h32-m8192-n8192-k24-ragged0-scale0-g4 | bf16 | 380.525 | 340.526 |
1.117x |
| h32-m8192-n8192-k24-ragged0-scale0-g4 | e4m3 | 337.151 | 310.256 |
1.087x |
| h16-m8192-n8192-k5-ragged0-scale0-g4 | bf16 | 61.920 | 52.384 | 1.182x
|
| h16-m8192-n8192-k5-ragged0-scale0-g4 | e4m3 | 54.656 | 51.264 | 1.066x
|
| h8-m4096-n4096-k64-ragged0-scale1-g4 | bf16 | 107.248 | 106.751 |
1.005x |
| h8-m4096-n4096-k64-ragged0-scale1-g4 | e4m3 | 101.519 | 100.768 |
1.007x |
| h8-m4096-n4096-k20-ragged1-scale0-g4 | bf16 | 29.648 | 25.824 | 1.148x
|
| h8-m4096-n4096-k20-ragged1-scale0-g4 | e4m3 | 27.360 | 24.576 | 1.113x
|
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g4 | bf16 | 24.768 | 22.656 |
1.093x |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g4 | e4m3 | 22.593 | 22.209 |
1.017x |
| h16-m1024-n8192-k12-ragged0-scale0-g4 | bf16 | 30.207 | 17.024 |
1.774x |
| h16-m1024-n8192-k12-ragged0-scale0-g4 | e4m3 | 19.008 | 15.264 |
1.245x |
| h32-m512-n8192-k16-ragged0-scale0-g4 | bf16 | 43.919 | 20.352 | 2.158x
|
| h32-m512-n8192-k16-ragged0-scale0-g4 | e4m3 | 25.536 | 18.656 | 1.369x
|
| h16-m1024-n8192-k1-ragged0-scale0-g4 | bf16 | 9.504 | 6.720 | 1.414x |
| h16-m1024-n8192-k1-ragged0-scale0-g4 | e4m3 | 6.560 | 5.345 | 1.227x |
| h8-m32768-n32768-k32-ragged0-scale0-g4 | bf16 | 547.677 | 453.518 |
1.208x |
| h8-m32768-n32768-k32-ragged0-scale0-g4 | e4m3 | 436.990 | 404.158 |
1.081x |
| h8-m32768-n32768-k64-ragged0-scale0-g4 | bf16 | 1057.469 | 913.902 |
1.157x |
| h8-m32768-n32768-k64-ragged0-scale0-g4 | e4m3 | 843.439 | 765.967 |
1.101x |
| h8-m32768-n32768-k64-ragged1-scale0-g4 | bf16 | 531.933 | 447.758 |
1.188x |
| h8-m32768-n32768-k64-ragged1-scale0-g4 | e4m3 | 439.166 | 401.214 |
1.095x |
| h8-m75648-n75648-k32-ragged0-scale0-g4 | bf16 | 1338.318 | 1175.949 |
1.138x |
| h8-m75648-n75648-k32-ragged0-scale0-g4 | e4m3 | 1008.559 | 916.559 |
1.100x |
| h8-m75648-n75648-k64-ragged0-scale0-g4 | bf16 | 2578.147 | 2198.198 |
1.173x |
| h8-m75648-n75648-k64-ragged0-scale0-g4 | e4m3 | 1901.783 | 1714.184 |
1.109x |
| h8-m75648-n75648-k64-ragged1-scale0-g4 | bf16 | 1323.487 | 1152.639 |
1.148x |
| h8-m75648-n75648-k64-ragged1-scale0-g4 | e4m3 | 1027.408 | 917.776 |
1.119x |
| h8-m109632-n109632-k32-ragged0-scale0-g4 | bf16 | 2013.384 | 1719.530
| 1.171x |
| h8-m109632-n109632-k32-ragged0-scale0-g4 | e4m3 | 1468.554 | 1334.651
| 1.100x |
| h8-m109632-n109632-k64-ragged0-scale0-g4 | bf16 | 3952.689 | 3391.617
| 1.165x |
| h8-m109632-n109632-k64-ragged0-scale0-g4 | e4m3 | 2892.063 | 2602.911
| 1.111x |
| h8-m109632-n109632-k64-ragged1-scale0-g4 | bf16 | 1929.130 | 1673.019
| 1.153x |
| h8-m109632-n109632-k64-ragged1-scale0-g4 | e4m3 | 1456.186 | 1313.227
| 1.109x |
| h12-m32768-n32768-k32-ragged0-scale0-g4 | bf16 | 828.033 | 733.632 |
1.129x |
| h12-m32768-n32768-k32-ragged0-scale0-g4 | e4m3 | 650.161 | 604.705 |
1.075x |
| h12-m32768-n32768-k64-ragged0-scale0-g4 | bf16 | 1578.987 | 1348.364 |
1.171x |
| h12-m32768-n32768-k64-ragged0-scale0-g4 | e4m3 | 1244.524 | 1130.124 |
1.101x |
| h12-m32768-n32768-k64-ragged1-scale0-g4 | bf16 | 840.769 | 730.928 |
1.150x |
| h12-m32768-n32768-k64-ragged1-scale0-g4 | e4m3 | 676.576 | 600.688 |
1.126x |
| h12-m75648-n75648-k32-ragged0-scale0-g4 | bf16 | 2006.587 | 1751.019 |
1.146x |
| h12-m75648-n75648-k32-ragged0-scale0-g4 | e4m3 | 1484.315 | 1350.779 |
1.099x |
| h12-m75648-n75648-k64-ragged0-scale0-g4 | bf16 | 3898.532 | 3425.874 |
1.138x |
| h12-m75648-n75648-k64-ragged0-scale0-g4 | e4m3 | 2964.079 | 2668.911 |
1.111x |
| h12-m75648-n75648-k64-ragged1-scale0-g4 | bf16 | 1978.987 | 1700.683 |
1.164x |
| h12-m75648-n75648-k64-ragged1-scale0-g4 | e4m3 | 1519.578 | 1364.203 |
1.114x |
| h12-m109632-n109632-k32-ragged0-scale0-g4 | bf16 | 3080.932 | 2657.619
| 1.159x |
| h12-m109632-n109632-k32-ragged0-scale0-g4 | e4m3 | 2267.873 | 2056.320
| 1.103x |
| h12-m109632-n109632-k64-ragged0-scale0-g4 | bf16 | 5889.122 | 4969.858
| 1.185x |
| h12-m109632-n109632-k64-ragged0-scale0-g4 | e4m3 | 4287.554 | 3854.322
| 1.112x |
| h12-m109632-n109632-k64-ragged1-scale0-g4 | bf16 | 2972.196 | 2630.963
| 1.130x |
| h12-m109632-n109632-k64-ragged1-scale0-g4 | e4m3 | 2282.881 | 2059.073
| 1.109x |
| h8-m256-n256-k3-ragged0-scale0-g8 | bf16 | 5.088 | 4.704 | 1.082x |
| h8-m256-n256-k3-ragged0-scale0-g8 | e4m3 | 4.736 | 4.288 | 1.104x |
| h8-m1024-n1024-k4-ragged0-scale0-g8 | bf16 | 7.200 | 6.368 | 1.131x |
| h8-m1024-n1024-k4-ragged0-scale0-g8 | e4m3 | 6.368 | 5.504 | 1.157x |
| h8-m1024-n1024-k12-ragged0-scale0-g8 | bf16 | 10.592 | 10.208 | 1.038x
|
| h8-m1024-n1024-k12-ragged0-scale0-g8 | e4m3 | 10.336 | 10.048 | 1.029x
|
| h8-m2048-n2048-k8-ragged0-scale0-g8 | bf16 | 14.144 | 12.608 | 1.122x
|
| h8-m2048-n2048-k8-ragged0-scale0-g8 | e4m3 | 13.665 | 11.440 | 1.195x
|
| h8-m2048-n2048-k16-ragged0-scale0-g8 | bf16 | 21.344 | 19.936 | 1.071x
|
| h8-m2048-n2048-k16-ragged0-scale0-g8 | e4m3 | 20.288 | 18.656 | 1.087x
|
| h8-m4096-n4096-k16-ragged0-scale0-g8 | bf16 | 37.024 | 33.376 | 1.109x
|
| h8-m4096-n4096-k16-ragged0-scale0-g8 | e4m3 | 35.360 | 31.936 | 1.107x
|
| h8-m4096-n4096-k32-ragged0-scale0-g8 | bf16 | 60.960 | 56.960 | 1.070x
|
| h8-m4096-n4096-k32-ragged0-scale0-g8 | e4m3 | 58.880 | 55.151 | 1.068x
|
| h16-m1024-n8192-k1-ragged0-scale0-g8 | bf16 | 9.312 | 6.463 | 1.441x |
| h16-m1024-n8192-k1-ragged0-scale0-g8 | e4m3 | 7.008 | 5.216 | 1.344x |
| h8-m512-n4096-k2-ragged0-scale0-g8 | bf16 | 5.888 | 4.704 | 1.252x |
| h8-m512-n4096-k2-ragged0-scale0-g8 | e4m3 | 4.929 | 4.096 | 1.203x |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g8 | bf16 | 27.233 | 26.592 |
1.024x |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g8 | e4m3 | 26.016 | 25.568 |
1.018x |
| h32-m2048-n2048-k8-ragged0-scale0-g8 | bf16 | 42.431 | 37.376 | 1.135x
|
| h32-m2048-n2048-k8-ragged0-scale0-g8 | e4m3 | 40.768 | 36.352 | 1.121x
|
| h16-m4096-n16384-k16-ragged0-scale0-g8 | bf16 | 85.184 | 59.167 |
1.440x |
| h16-m4096-n16384-k16-ragged0-scale0-g8 | e4m3 | 70.144 | 56.544 |
1.241x |
| h8-m1024-n32768-k64-ragged0-scale0-g8 | bf16 | 56.128 | 33.472 |
1.677x |
| h8-m1024-n32768-k64-ragged0-scale0-g8 | e4m3 | 34.816 | 31.744 |
1.097x |
| h8-m2048-n32768-k48-ragged1-scale0-g8 | bf16 | 53.184 | 30.176 |
1.762x |
| h8-m2048-n32768-k48-ragged1-scale0-g8 | e4m3 | 38.352 | 29.248 |
1.311x |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | bf16 | 378.142 | 335.871 |
1.126x |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | e4m3 | 338.655 | 311.519 |
1.087x |
| h16-m8192-n8192-k5-ragged0-scale0-g8 | bf16 | 61.664 | 52.353 | 1.178x
|
| h16-m8192-n8192-k5-ragged0-scale0-g8 | e4m3 | 54.721 | 51.200 | 1.069x
|
| h8-m8192-n8192-k2-ragged0-scale0-g8 | bf16 | 28.032 | 19.328 | 1.450x
|
| h8-m8192-n8192-k2-ragged0-scale0-g8 | e4m3 | 21.968 | 15.680 | 1.401x
|
| h8-m4096-n4096-k64-ragged0-scale1-g8 | bf16 | 107.617 | 107.024 |
1.006x |
| h8-m4096-n4096-k64-ragged0-scale1-g8 | e4m3 | 101.552 | 100.832 |
1.007x |
| h8-m4096-n4096-k20-ragged1-scale0-g8 | bf16 | 29.568 | 25.248 | 1.171x
|
| h8-m4096-n4096-k20-ragged1-scale0-g8 | e4m3 | 26.656 | 24.576 | 1.085x
|
| h8-m512-n512-k1-ragged0-scale0-g8 | bf16 | 4.128 | 3.584 | 1.152x |
| h8-m512-n512-k1-ragged0-scale0-g8 | e4m3 | 3.680 | 3.200 | 1.150x |
| h8-m512-n1024-k2-ragged0-scale0-g8 | bf16 | 5.440 | 4.576 | 1.189x |
| h8-m512-n1024-k2-ragged0-scale0-g8 | e4m3 | 4.703 | 3.968 | 1.185x |
| h16-m256-n512-k2-ragged1-scale0-g8 | bf16 | 5.408 | 4.607 | 1.174x |
| h16-m256-n512-k2-ragged1-scale0-g8 | e4m3 | 4.736 | 4.000 | 1.184x |
| h8-m1024-n2048-k4-ragged0-scale0-g8 | bf16 | 8.192 | 6.432 | 1.274x |
| h8-m1024-n2048-k4-ragged0-scale0-g8 | e4m3 | 7.008 | 5.600 | 1.251x |
| h8-m1024-n4096-k6-ragged0-scale0-g8 | bf16 | 11.392 | 7.712 | 1.477x |
| h8-m1024-n4096-k6-ragged0-scale0-g8 | e4m3 | 8.288 | 7.072 | 1.172x |
| h8-m256-n4096-k8-ragged0-scale0-g8 | bf16 | 7.776 | 5.984 | 1.299x |
| h8-m256-n4096-k8-ragged0-scale0-g8 | e4m3 | 6.784 | 5.600 | 1.211x |
| h8-m256-n2048-k8-ragged0-scale0-g8 | bf16 | 7.424 | 6.048 | 1.228x |
| h8-m256-n2048-k8-ragged0-scale0-g8 | e4m3 | 6.656 | 5.600 | 1.189x |
| h8-m512-n4096-k8-ragged0-scale0-g8 | bf16 | 9.824 | 6.656 | 1.476x |
| h8-m512-n4096-k8-ragged0-scale0-g8 | e4m3 | 7.936 | 6.144 | 1.292x |
| h16-m256-n2048-k7-ragged1-scale0-g8 | bf16 | 7.968 | 6.208 | 1.284x |
| h16-m256-n2048-k7-ragged1-scale0-g8 | e4m3 | 6.912 | 5.664 | 1.220x |
| h8-m256-n4096-k9-ragged0-scale0-g8 | bf16 | 8.128 | 6.176 | 1.316x |
| h8-m256-n4096-k9-ragged0-scale0-g8 | e4m3 | 6.720 | 5.664 | 1.186x |
| h8-m512-n4096-k12-ragged0-scale0-g8 | bf16 | 11.808 | 7.648 | 1.544x |
| h8-m512-n4096-k12-ragged0-scale0-g8 | e4m3 | 8.383 | 7.136 | 1.175x |
| h8-m256-n2048-k10-ragged0-scale0-g8 | bf16 | 8.192 | 6.656 | 1.231x |
| h8-m256-n2048-k10-ragged0-scale0-g8 | e4m3 | 7.104 | 6.304 | 1.127x |
| h8-m256-n4096-k16-ragged0-scale0-g8 | bf16 | 12.160 | 9.248 | 1.315x |
| h8-m256-n4096-k16-ragged0-scale0-g8 | e4m3 | 9.248 | 8.256 | 1.120x |
| h8-m128-n4096-k17-ragged0-scale0-g8 | bf16 | 9.279 | 6.655 | 1.394x |
| h8-m128-n4096-k17-ragged0-scale0-g8 | e4m3 | 7.360 | 6.464 | 1.139x |
| h8-m256-n16384-k32-ragged0-scale0-g8 | bf16 | 22.560 | 17.312 | 1.303x
|
| h8-m256-n16384-k32-ragged0-scale0-g8 | e4m3 | 18.112 | 17.216 | 1.052x
|
| h8-m128-n32768-k64-ragged0-scale0-g8 | bf16 | 28.960 | 20.448 | 1.416x
|
| h8-m128-n32768-k64-ragged0-scale0-g8 | e4m3 | 20.896 | 17.856 | 1.170x
|
| h8-m256-n4096-k12-ragged0-scale0-uneven-g8 | bf16 | 7.776 | 6.624 |
1.174x |
| h8-m256-n4096-k12-ragged0-scale0-uneven-g8 | e4m3 | 6.816 | 6.304 |
1.081x |
| h8-m512-n8192-k24-ragged0-scale0-uneven-g8 | bf16 | 13.728 | 10.081 |
1.362x |
| h8-m512-n8192-k24-ragged0-scale0-uneven-g8 | e4m3 | 10.496 | 8.832 |
1.188x |
| h8-m256-n4096-k8-ragged0-scale1-g8 | bf16 | 7.776 | 6.017 | 1.292x |
| h8-m256-n4096-k8-ragged0-scale1-g8 | e4m3 | 6.752 | 5.664 | 1.192x |
| h32-m2048-n2048-k8-ragged0-scale0-g8 | bf16 | 42.431 | 37.376 | 1.135x
|
| h32-m2048-n2048-k8-ragged0-scale0-g8 | e4m3 | 40.768 | 36.352 | 1.121x
|
| h16-m4096-n16384-k16-ragged0-scale0-g8 | bf16 | 85.184 | 59.167 |
1.440x |
| h16-m4096-n16384-k16-ragged0-scale0-g8 | e4m3 | 70.144 | 56.544 |
1.241x |
| h8-m1024-n32768-k64-ragged0-scale0-g8 | bf16 | 56.128 | 33.472 |
1.677x |
| h8-m1024-n32768-k64-ragged0-scale0-g8 | e4m3 | 34.816 | 31.744 |
1.097x |
| h8-m2048-n32768-k48-ragged1-scale0-g8 | bf16 | 53.184 | 30.176 |
1.762x |
| h8-m2048-n32768-k48-ragged1-scale0-g8 | e4m3 | 38.352 | 29.248 |
1.311x |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | bf16 | 378.142 | 335.871 |
1.126x |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | e4m3 | 338.655 | 311.519 |
1.087x |
| h16-m8192-n8192-k5-ragged0-scale0-g8 | bf16 | 61.664 | 52.353 | 1.178x
|
| h16-m8192-n8192-k5-ragged0-scale0-g8 | e4m3 | 54.721 | 51.200 | 1.069x
|
| h8-m4096-n4096-k64-ragged0-scale1-g8 | bf16 | 107.617 | 107.024 |
1.006x |
| h8-m4096-n4096-k64-ragged0-scale1-g8 | e4m3 | 101.552 | 100.832 |
1.007x |
| h8-m4096-n4096-k20-ragged1-scale0-g8 | bf16 | 29.568 | 25.248 | 1.171x
|
| h8-m4096-n4096-k20-ragged1-scale0-g8 | e4m3 | 26.656 | 24.576 | 1.085x
|
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g8 | bf16 | 27.233 | 26.592 |
1.024x |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g8 | e4m3 | 26.016 | 25.568 |
1.018x |
| h16-m1024-n8192-k12-ragged0-scale0-g8 | bf16 | 29.376 | 16.160 |
1.818x |
| h16-m1024-n8192-k12-ragged0-scale0-g8 | e4m3 | 18.784 | 15.008 |
1.252x |
| h32-m512-n8192-k16-ragged0-scale0-g8 | bf16 | 43.648 | 18.944 | 2.304x
|
| h32-m512-n8192-k16-ragged0-scale0-g8 | e4m3 | 25.920 | 17.824 | 1.454x
|
| h16-m1024-n8192-k1-ragged0-scale0-g8 | bf16 | 9.312 | 6.463 | 1.441x |
| h16-m1024-n8192-k1-ragged0-scale0-g8 | e4m3 | 7.008 | 5.216 | 1.344x |
| h8-m32768-n32768-k32-ragged0-scale0-g8 | bf16 | 553.006 | 454.383 |
1.217x |
| h8-m32768-n32768-k32-ragged0-scale0-g8 | e4m3 | 445.935 | 405.774 |
1.099x |
| h8-m32768-n32768-k64-ragged0-scale0-g8 | bf16 | 1059.328 | 916.865 |
1.155x |
| h8-m32768-n32768-k64-ragged0-scale0-g8 | e4m3 | 839.423 | 762.799 |
1.100x |
| h8-m32768-n32768-k64-ragged1-scale0-g8 | bf16 | 556.606 | 457.918 |
1.216x |
| h8-m32768-n32768-k64-ragged1-scale0-g8 | e4m3 | 456.094 | 408.622 |
1.116x |
| h8-m75648-n75648-k32-ragged0-scale0-g8 | bf16 | 1331.361 | 1162.866 |
1.145x |
| h8-m75648-n75648-k32-ragged0-scale0-g8 | e4m3 | 1010.928 | 919.247 |
1.100x |
| h8-m75648-n75648-k64-ragged0-scale0-g8 | bf16 | 2573.113 | 2197.258 |
1.171x |
| h8-m75648-n75648-k64-ragged0-scale0-g8 | e4m3 | 1911.033 | 1722.362 |
1.110x |
| h8-m75648-n75648-k64-ragged1-scale0-g8 | bf16 | 1314.194 | 1133.473 |
1.159x |
| h8-m75648-n75648-k64-ragged1-scale0-g8 | e4m3 | 1026.704 | 914.656 |
1.123x |
| h8-m109632-n109632-k32-ragged0-scale0-g8 | bf16 | 2003.722 | 1685.259
| 1.189x |
| h8-m109632-n109632-k32-ragged0-scale0-g8 | e4m3 | 1457.835 | 1319.691
| 1.105x |
| h8-m109632-n109632-k64-ragged0-scale0-g8 | bf16 | 3898.181 | 3347.413
| 1.165x |
| h8-m109632-n109632-k64-ragged0-scale0-g8 | e4m3 | 2891.664 | 2599.585
| 1.112x |
| h8-m109632-n109632-k64-ragged1-scale0-g8 | bf16 | 1891.259 | 1630.988
| 1.160x |
| h8-m109632-n109632-k64-ragged1-scale0-g8 | e4m3 | 1430.172 | 1289.308
| 1.109x |

The family's other Cake variants are the BF16 and Sage-FP8 MHA programs
shipped by earlier PRs of this backend, and the family runs only on
sm_90a (Hopper), while other architectures have their own Cake
block-sparse attention backends.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added grouped-query attention support to the SM90 Cake backend for
query-to-KV head ratios of 2, 4, and 8, alongside existing multi-head
attention support. The feature covers BF16 and Sage FP8 routes, with
KV-head-shaped masks and inputs.
* Expanded the benchmark to exercise GQA workloads and compare
replicated MHA and FP8 variants. Benchmark reports now include GQA and
KV-head counts, planned stages, and updated timing details.
* **Documentation**
* Updated backend and sparse-attention guidance to describe supported
head layouts and ratio requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [195ccac](https://github.com/flashinfer-ai/flashinfer/commit/195ccacadc3b9c826a492885c8e89a8b32041ac4)

- **作者**: eigen
- **时间**: 2026-10-24T12:06:47Z
- **提交信息**: feat(cake_gdn): context-parallel packed GDN auto grad with precise cross-rank state passing, native grouped Q/K heads and per-document zigzag for Qwen hybrid GQA/GDN with grad (#7169)

This PR adds Cake's context-parallel GDN training kernel as the
standalone package `flashinfer/experimental/cake_gdn_train`, with the
facade `flashinfer/gdn_train.py`. The kernel has one data-type variant:
BF16 q/k/v/out/dout, an FP32 scalar log-decay `g` and `beta`, and FP32
dq/dk reduction across the value heads of a Q/K head, with grouped
`(H_qk, HV)` as runtime parameters. It supports three partition layouts
(contiguous, whole-buffer zigzag, and per-document zigzag + ragged) and
fused forward, backward-from-saved-set, checkpoint-replay (non-reentrant
and reentrant) and optional causal-conv1d halo-exchange forms, with
exact cross-rank state passing; this PR delivers all of them. Against
the FLA GDN context-parallel path (there is no previous Cake version),
the geometric-mean speedup is 2.84x forward and 3.57x per training step
on GB300, and 3.00x forward and 3.93x per training step on GB200.

**NVIDIA GB300 (sm_103a, CUDA 13.4)** — context-parallel GDN layer,
`(H_qk, HV) = (16, 48)`, head dim 128, CP = 2, 4, 8, 16; latency per
call of the slowest rank (median over repeats). Forward = module
forward; training step = forward + checkpoint recompute + backward,
communication included. Baseline: the FLA GDN context-parallel path on
the same layout (per-document rows against the faster of its contiguous
/ zigzag layouts).

| Pack (tokens / docs) | CP | Layout | Forward: this PR ms | FLA ms |
Speedup | Training step: this PR ms | FLA ms | Speedup |
|---|---:|---|---:|---:|---:|---:|---:|---:|
| P1 (241,817 tokens / 6 docs) | 2 | contiguous | 9.124 | 33.765 | 3.70x
| 28.135 | 104.862 | 3.73x |
| P1 (241,817 tokens / 6 docs) | 2 | zigzag | 9.167 | 25.878 | 2.82x |
28.370 | 101.086 | 3.56x |
| P1 (241,817 tokens / 6 docs) | 2 | per-document zigzag + ragged |
9.438 | 25.878 | 2.74x | 28.878 | 101.086 | 3.50x |
| P1 (241,817 tokens / 6 docs) | 4 | contiguous | 5.239 | 17.126 | 3.27x
| 15.818 | 65.730 | 4.16x |
| P1 (241,817 tokens / 6 docs) | 4 | zigzag | 5.386 | 16.354 | 3.04x |
16.195 | 59.362 | 3.67x |
| P1 (241,817 tokens / 6 docs) | 4 | per-document zigzag + ragged |
5.073 | 16.354 | 3.22x | 15.445 | 59.362 | 3.84x |
| P1 (241,817 tokens / 6 docs) | 8 | contiguous | 2.972 | 8.962 | 3.01x
| 8.639 | 33.671 | 3.90x |
| P1 (241,817 tokens / 6 docs) | 8 | zigzag | 3.198 | 9.321 | 2.91x |
9.218 | 34.462 | 3.74x |
| P1 (241,817 tokens / 6 docs) | 8 | per-document zigzag + ragged |
3.030 | 8.962 | 2.96x | 8.941 | 33.671 | 3.77x |
| P1 (241,817 tokens / 6 docs) | 16 | contiguous | 2.360 | 4.884 | 2.07x
| 7.396 | 17.727 | 2.40x |
| P1 (241,817 tokens / 6 docs) | 16 | zigzag | 1.992 | 5.717 | 2.87x |
6.122 | 19.965 | 3.26x |
| P1 (241,817 tokens / 6 docs) | 16 | per-document zigzag + ragged |
2.221 | 4.884 | 2.20x | 7.167 | 17.727 | 2.47x |
| P2 (261,987 / 3) | 2 | contiguous | 9.859 | 32.310 | 3.28x | 30.561 |
111.746 | 3.66x |
| P2 (261,987 / 3) | 2 | zigzag | 10.091 | 32.054 | 3.18x | 30.960 |
122.134 | 3.94x |
| P2 (261,987 / 3) | 2 | per-document zigzag + ragged | 10.112 | 32.054
| 3.17x | 31.366 | 111.746 | 3.56x |
| P2 (261,987 / 3) | 4 | contiguous | 5.133 | 18.612 | 3.63x | 15.663 |
71.359 | 4.56x |
| P2 (261,987 / 3) | 4 | zigzag | 5.523 | 18.772 | 3.40x | 16.755 |
71.270 | 4.25x |
| P2 (261,987 / 3) | 4 | per-document zigzag + ragged | 5.850 | 18.612 |
3.18x | 17.517 | 71.270 | 4.07x |
| P2 (261,987 / 3) | 8 | contiguous | 2.957 | 9.623 | 3.25x | 8.652 |
36.397 | 4.21x |
| P2 (261,987 / 3) | 8 | zigzag | 3.435 | 10.103 | 2.94x | 9.878 |
37.169 | 3.76x |
| P2 (261,987 / 3) | 8 | per-document zigzag + ragged | 3.316 | 9.623 |
2.90x | 9.689 | 36.397 | 3.76x |
| P2 (261,987 / 3) | 16 | contiguous | 2.306 | 5.234 | 2.27x | 7.325 |
19.047 | 2.60x |
| P2 (261,987 / 3) | 16 | zigzag | 2.102 | 6.026 | 2.87x | 6.353 |
21.258 | 3.35x |
| P2 (261,987 / 3) | 16 | per-document zigzag + ragged | 2.188 | 5.234 |
2.39x | 6.796 | 19.047 | 2.80x |
| P3 (259,174 / 2) | 2 | contiguous | 8.130 | 11.684 | 1.44x | 29.485 |
91.328 | 3.10x |
| P3 (259,174 / 2) | 2 | zigzag | 10.812 | 24.606 | 2.28x | 33.212 |
115.900 | 3.49x |
| P3 (259,174 / 2) | 2 | per-document zigzag + ragged | 9.724 | 11.684 |
1.20x | 30.191 | 91.328 | 3.03x |
| P3 (259,174 / 2) | 4 | contiguous | 5.472 | 18.390 | 3.36x | 16.718 |
70.655 | 4.23x |
| P3 (259,174 / 2) | 4 | zigzag | 6.050 | 18.720 | 3.09x | 18.110 |
70.741 | 3.91x |
| P3 (259,174 / 2) | 4 | per-document zigzag + ragged | 5.949 | 18.390 |
3.09x | 17.645 | 70.655 | 4.00x |
| P3 (259,174 / 2) | 8 | contiguous | 2.942 | 9.536 | 3.24x | 8.570 |
36.135 | 4.22x |
| P3 (259,174 / 2) | 8 | zigzag | 3.380 | 10.027 | 2.97x | 9.805 |
36.937 | 3.77x |
| P3 (259,174 / 2) | 8 | per-document zigzag + ragged | 3.393 | 9.536 |
2.81x | 9.888 | 36.135 | 3.65x |
| P3 (259,174 / 2) | 16 | contiguous | 2.354 | 5.191 | 2.20x | 7.305 |
18.877 | 2.58x |
| P3 (259,174 / 2) | 16 | zigzag | 2.072 | 5.993 | 2.89x | 6.246 |
21.034 | 3.37x |
| P3 (259,174 / 2) | 16 | per-document zigzag + ragged | 2.179 | 5.191 |
2.38x | 6.489 | 18.877 | 2.91x |
| P4 (254,976 / 1) | 2 | contiguous | 9.557 | 35.582 | 3.72x | 29.687 |
138.315 | 4.66x |
| P4 (254,976 / 1) | 2 | zigzag | 9.980 | 35.895 | 3.60x | 30.661 |
137.541 | 4.49x |
| P4 (254,976 / 1) | 2 | per-document zigzag + ragged | 10.017 | 35.582
| 3.55x | 30.777 | 137.541 | 4.47x |
| P4 (254,976 / 1) | 4 | contiguous | 5.001 | 18.156 | 3.63x | 15.252 |
69.661 | 4.57x |
| P4 (254,976 / 1) | 4 | zigzag | 5.017 | 18.331 | 3.65x | 15.303 |
69.534 | 4.54x |
| P4 (254,976 / 1) | 4 | per-document zigzag + ragged | 5.200 | 18.156 |
3.49x | 15.866 | 69.534 | 4.38x |
| P4 (254,976 / 1) | 8 | contiguous | 2.875 | 9.424 | 3.28x | 8.344 |
35.534 | 4.26x |
| P4 (254,976 / 1) | 8 | zigzag | 3.373 | 9.795 | 2.90x | 9.702 | 36.314
| 3.74x |
| P4 (254,976 / 1) | 8 | per-document zigzag + ragged | 3.406 | 9.424 |
2.77x | 9.921 | 35.534 | 3.58x |
| P4 (254,976 / 1) | 16 | contiguous | 2.281 | 5.148 | 2.26x | 7.223 |
18.752 | 2.60x |
| P4 (254,976 / 1) | 16 | zigzag | 2.122 | 5.939 | 2.80x | 6.232 |
20.841 | 3.34x |
| P4 (254,976 / 1) | 16 | per-document zigzag + ragged | 2.525 | 5.148 |
2.04x | 7.653 | 18.752 | 2.45x |
| P5 (249,856 / 4) | 2 | contiguous | 9.576 | 21.673 | 2.26x | 29.735 |
85.079 | 2.86x |
| P5 (249,856 / 4) | 2 | zigzag | 10.382 | 33.298 | 3.21x | 31.688 |
117.450 | 3.71x |
| P5 (249,856 / 4) | 2 | per-document zigzag + ragged | 9.741 | 21.673 |
2.22x | 29.969 | 85.079 | 2.84x |
| P5 (249,856 / 4) | 4 | contiguous | 5.253 | 17.244 | 3.28x | 16.094 |
66.956 | 4.16x |
| P5 (249,856 / 4) | 4 | zigzag | 5.757 | 17.989 | 3.12x | 17.259 |
68.041 | 3.94x |
| P5 (249,856 / 4) | 4 | per-document zigzag + ragged | 5.236 | 17.244 |
3.29x | 15.950 | 66.956 | 4.20x |
| P5 (249,856 / 4) | 8 | contiguous | 2.879 | 9.221 | 3.20x | 8.517 |
34.770 | 4.08x |
| P5 (249,856 / 4) | 8 | zigzag | 3.295 | 9.609 | 2.92x | 9.481 | 35.402
| 3.73x |
| P5 (249,856 / 4) | 8 | per-document zigzag + ragged | 3.041 | 9.221 |
3.03x | 8.969 | 34.770 | 3.88x |
| P5 (249,856 / 4) | 16 | contiguous | 2.295 | 4.995 | 2.18x | 7.220 |
18.144 | 2.51x |
| P5 (249,856 / 4) | 16 | zigzag | 2.032 | 5.741 | 2.83x | 6.167 |
20.180 | 3.27x |
| P5 (249,856 / 4) | 16 | per-document zigzag + ragged | 2.120 | 4.995 |
2.36x | 6.834 | 18.144 | 2.65x |

Geometric-mean speedup over 60 rows: forward 2.84x, training step 3.57x.

**NVIDIA GB200 (sm_100a, CUDA 13.4)** — context-parallel GDN layer,
`(H_qk, HV) = (16, 48)`, head dim 128, CP = 2, 4, 8; latency per call of
the slowest rank (median over repeats). Forward = module forward;
training step = forward + checkpoint recompute + backward, communication
included. Baseline: the FLA GDN context-parallel path on the same layout
(per-document rows against the faster of its contiguous / zigzag
layouts).

| Pack (tokens / docs) | CP | Layout | Forward: this PR ms | FLA ms |
Speedup | Training step: this PR ms | FLA ms | Speedup |
|---|---:|---|---:|---:|---:|---:|---:|---:|
| P1 (241,817 tokens / 6 docs) | 2 | contiguous | 9.272 | 34.180 | 3.69x
| 28.737 | 109.869 | 3.82x |
| P1 (241,817 tokens / 6 docs) | 2 | zigzag | 9.305 | 26.515 | 2.85x |
28.952 | 104.400 | 3.61x |
| P1 (241,817 tokens / 6 docs) | 2 | per-document zigzag + ragged |
9.638 | 26.515 | 2.75x | 29.599 | 104.400 | 3.53x |
| P1 (241,817 tokens / 6 docs) | 4 | contiguous | 5.315 | 17.405 | 3.27x
| 16.105 | 68.453 | 4.25x |
| P1 (241,817 tokens / 6 docs) | 4 | zigzag | 5.472 | 16.643 | 3.04x |
16.495 | 60.668 | 3.68x |
| P1 (241,817 tokens / 6 docs) | 4 | per-document zigzag + ragged |
5.172 | 16.643 | 3.22x | 15.778 | 60.668 | 3.85x |
| P1 (241,817 tokens / 6 docs) | 8 | contiguous | 2.978 | 9.058 | 3.04x
| 8.738 | 34.890 | 3.99x |
| P1 (241,817 tokens / 6 docs) | 8 | zigzag | 3.212 | 9.434 | 2.94x |
9.293 | 34.866 | 3.75x |
| P1 (241,817 tokens / 6 docs) | 8 | per-document zigzag + ragged |
3.039 | 9.058 | 2.98x | 9.045 | 34.866 | 3.85x |
| P2 (261,987 / 3) | 2 | contiguous | 10.009 | 32.577 | 3.25x | 31.236 |
117.889 | 3.77x |
| P2 (261,987 / 3) | 2 | zigzag | 10.242 | 32.776 | 3.20x | 31.605 |
125.072 | 3.96x |
| P2 (261,987 / 3) | 2 | per-document zigzag + ragged | 10.286 | 32.577
| 3.17x | 32.075 | 117.889 | 3.68x |
| P2 (261,987 / 3) | 4 | contiguous | 5.226 | 18.870 | 3.61x | 16.019 |
74.370 | 4.64x |
| P2 (261,987 / 3) | 4 | zigzag | 5.631 | 19.048 | 3.38x | 17.075 |
72.574 | 4.25x |
| P2 (261,987 / 3) | 4 | per-document zigzag + ragged | 5.938 | 18.870 |
3.18x | 17.835 | 72.574 | 4.07x |
| P2 (261,987 / 3) | 8 | contiguous | 2.965 | 9.743 | 3.29x | 8.773 |
37.684 | 4.30x |
| P2 (261,987 / 3) | 8 | zigzag | 3.437 | 10.251 | 2.98x | 9.957 |
37.683 | 3.78x |
| P2 (261,987 / 3) | 8 | per-document zigzag + ragged | 3.334 | 9.743 |
2.92x | 9.790 | 37.683 | 3.85x |
| P3 (259,174 / 2) | 2 | contiguous | 8.298 | 11.913 | 1.44x | 30.111 |
96.560 | 3.21x |
| P3 (259,174 / 2) | 2 | zigzag | 10.932 | 25.041 | 2.29x | 33.812 |
118.439 | 3.50x |
| P3 (259,174 / 2) | 2 | per-document zigzag + ragged | 9.871 | 11.913 |
1.21x | 30.845 | 96.560 | 3.13x |
| P3 (259,174 / 2) | 4 | contiguous | 5.546 | 18.701 | 3.37x | 17.067 |
73.625 | 4.31x |
| P3 (259,174 / 2) | 4 | zigzag | 6.150 | 19.004 | 3.09x | 18.402 |
72.123 | 3.92x |
| P3 (259,174 / 2) | 4 | per-document zigzag + ragged | 6.040 | 18.701 |
3.10x | 18.130 | 72.123 | 3.98x |
| P3 (259,174 / 2) | 8 | contiguous | 2.961 | 9.631 | 3.25x | 8.708 |
37.331 | 4.29x |
| P3 (259,174 / 2) | 8 | zigzag | 3.399 | 10.162 | 2.99x | 9.891 |
37.436 | 3.78x |
| P3 (259,174 / 2) | 8 | per-document zigzag + ragged | 3.413 | 9.631 |
2.82x | 10.013 | 37.331 | 3.73x |
| P4 (254,976 / 1) | 2 | contiguous | 9.720 | 35.896 | 3.69x | 30.346 |
143.813 | 4.74x |
| P4 (254,976 / 1) | 2 | zigzag | 10.106 | 36.569 | 3.62x | 31.265 |
140.296 | 4.49x |
| P4 (254,976 / 1) | 2 | per-document zigzag + ragged | 10.157 | 35.896
| 3.53x | 31.379 | 140.296 | 4.47x |
| P4 (254,976 / 1) | 4 | contiguous | 5.091 | 18.442 | 3.62x | 15.595 |
72.400 | 4.64x |
| P4 (254,976 / 1) | 4 | zigzag | 5.136 | 18.690 | 3.64x | 15.685 |
70.856 | 4.52x |
| P4 (254,976 / 1) | 4 | per-document zigzag + ragged | 5.300 | 18.442 |
3.48x | 16.231 | 70.856 | 4.37x |
| P4 (254,976 / 1) | 8 | contiguous | 2.870 | 9.533 | 3.32x | 8.472 |
36.717 | 4.33x |
| P4 (254,976 / 1) | 8 | zigzag | 3.369 | 9.914 | 2.94x | 9.792 | 36.777
| 3.76x |
| P4 (254,976 / 1) | 8 | per-document zigzag + ragged | 3.442 | 9.533 |
2.77x | 10.015 | 36.717 | 3.67x |
| P5 (249,856 / 4) | 2 | contiguous | 9.732 | 22.057 | 2.27x | 30.332 |
92.585 | 3.05x |
| P5 (249,856 / 4) | 2 | zigzag | 10.531 | 33.970 | 3.23x | 32.305 |
120.193 | 3.72x |
| P5 (249,856 / 4) | 2 | per-document zigzag + ragged | 9.902 | 22.057 |
2.23x | 30.610 | 92.585 | 3.02x |
| P5 (249,856 / 4) | 4 | contiguous | 5.340 | 17.430 | 3.26x | 16.434 |
70.706 | 4.30x |
| P5 (249,856 / 4) | 4 | zigzag | 5.851 | 18.267 | 3.12x | 17.521 |
69.187 | 3.95x |
| P5 (249,856 / 4) | 4 | per-document zigzag + ragged | 5.331 | 17.430 |
3.27x | 16.298 | 69.187 | 4.24x |
| P5 (249,856 / 4) | 8 | contiguous | 2.870 | 9.347 | 3.26x | 8.609 |
36.378 | 4.23x |
| P5 (249,856 / 4) | 8 | zigzag | 3.297 | 9.735 | 2.95x | 9.543 | 35.840
| 3.76x |
| P5 (249,856 / 4) | 8 | per-document zigzag + ragged | 3.049 | 9.347 |
3.07x | 9.111 | 35.840 | 3.93x |

Geometric-mean speedup over 45 rows: forward 3.00x, training step 3.93x.

Cake's GDN inference kernels (chunked prefill / decode) ship separately,
and Cake's KDA context-parallel training sibling
(`flashinfer/experimental/cake_kda_train`) covers the per-channel-gate
form; this kernel is built for sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an experimental API for packed, context-parallel GDN training,
including forward and backward operations, configurable options, and
memory and communication estimates.
* Added support for distributed execution across selected NVIDIA GPU
architectures, with multiple partitioning layouts and checkpoint/replay
options.
* Added a benchmark for comparing training performance across execution
modes.
* **Documentation**
* Added guidance on the experimental API, supported configurations,
constraints, and known limitations.
* **Tests**
* Added reference-based accuracy checks and coverage for API behavior,
partitioning, and build configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e415578](https://github.com/flashinfer-ai/flashinfer/commit/e415578a3adfaad61cf13f636305874e82742054)

- **作者**: Yang Xu
- **时间**: 2026-10-24T12:04:59Z
- **提交信息**: feat(moe): add DeepSeek block FP8 to Frost low latency (#7174)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add explicit `frost_low_latency` support for `DeepSeekFp8`
weights/activations with canonical E4M3 checkpoint payloads and
arbitrary FP32 128×128 weight scales. BF16 input is quantized per 128
values; prepared E4M3 input instead uses its supplied scales. Both
entries preserve FP32 FC1 preactivation, then quantize the activated
intermediate before FC2. The same numerical contract applies to
SM90/100/103/107/120.

Supports all ten typed activations, packed/unpacked routing and
raw/final outputs at T≤8/top-k≤32, H/I divisible by 128. Preparation
does not requantize the weights. Four kernels for BF16 entry, three for
prepared E4M3; compiled metadata retains no runtime tensor bindings.
Default automatic backend selection is unchanged.

Complete routed-expert GPU intervals on RTX PRO 6000 Blackwell
Workstation (SM120), comparing tuned stock SM12x FP8 with the integrated
Frost path:

| H/I, E/K | T/routes | Cache | Native µs | Frost µs | Speedup |
|---|---|---|---:|---:|---:|
| 2048/512, 512/10 | 1 | warm | 26.512 | 10.176 | 2.605× |
| 2048/512, 512/10 | 1 | cold | 34.792 | 27.984 | 1.243× |
| 2048/512, 512/10 | 8/shared | warm | 24.016 | 39.096 | 0.614× |
| 7168/2048, 256/8 | 1 | warm | 229.070 | 219.958 | 1.041× |
| 7168/2048, 256/8 | 4/shared | warm | 229.662 | 399.141 | 0.575× |

CUPTI first-to-last GPU activity spans, 48 native candidates and 16
Frost candidates, frozen ABBA validation. Both use FP32 preactivation;
native FP32 expert/atomic BF16 combine differs from Frost BF16
expert/ordered FP32 combine, with separate references retained. These
are synthetic model-shaped kernel tests, not model throughput, EP
communication or decode-step measurements. Larger/shared-expert losses
are retained to bound applicability. Full measurements and the
reproducer are included in this PR.

## 🔍 Related Issues

Builds on the merged W8A16 infrastructure from #7166. The unrelated
native cuTile compiler repair merged separately in #7168.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Targeted native-device tests pass; required CI will be requested
on the final head.

Final 27 new cases pass on SM120; B300 consolidated nine-file suite: 267
passed, 3 architecture-specific skips, including all 27 new cases. H100
passed the earlier 23 cases plus all eight final public-entry forms.
Cases cover changing scales/inputs/routes under graph replay, all typed
activations, packed/unpacked and raw/final outputs, invalid expert IDs
with NaN/Inf scores, fresh storage hitting warm metadata and T8/top-k32
at extreme FMA widths. Scoped pre-commit checks pass. The seven stored
timing cases retain their measured source hashes. Rebasing onto main
after #7166 merged did not change the Frost implementation, tests,
benchmark or native SM12x FP8 path. The final rebased head passes all 27
new tests plus 3 generated activation-matrix checks on SM120.

SM100/SM107 qualification awaits independent CI. No skipped lane is
counted as device execution. The public benchmark was also exercised
independently at T2/disjoint (32.112→14.688µs). On the final rebased
head, T1 warm reproduces 26.5115→10.18375µs (2.603×), consistent with
the stored result.

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

Review scale-layout/pointer freshness, the explicit FP32 FC1 boundary
and invalid-route masking. The static quantization floor is
max(amax,1e-4)/448 with round-to-nearest division. A separate B300
prototype used an additional FP8 preactivation boundary to match
TRT-LLM; it is not included or silently selected here. No Tensor Core
implementation or monokernel is added. Scoped hooks were used instead of
reformatting unrelated files.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added DeepSeek FP8 support to Frost low-latency execution, including
weight preparation and support for BF16 or prequantized E4M3 inputs.
- Expanded SM90 documentation and compatibility information for DeepSeek
FP8 workloads.
- **Bug Fixes**
- Added validation for input and weight formats, shapes, and device
requirements.
- **Tests**
- Added coverage for output accuracy, supported activations, routing
modes, CUDA Graph replay, and invalid inputs.
- **Benchmarks**
- Added an SM120 benchmark comparing Frost and native execution across
tactics and reporting timing and accuracy results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [04b4d62](https://github.com/flashinfer-ai/flashinfer/commit/04b4d62cebc9e1737480672beb58fe646d91ca2d)

- **作者**: eigen
- **时间**: 2026-10-24T11:59:56Z
- **提交信息**: feat(cake_tp_moe_finalize_rmsnorm): deliver the TP4 programs on sm_107a (#7173)

This PR adds TP4 programs and routes on sm_107a (NVIDIA R200, four GPUs
per node) to the Cake backend for
`flashinfer.comm.tp_moe_finalize_rmsnorm`. This is the tensor-parallel
MoE finalize + RMSNorm collective (hidden size 4096, top-8 experts), and
its Cake backend already ships on sm_100a and sm_103a from PR #7120. The
kernel has two routing-weight data types (BF16 and FP32
`expert_weights`) and two norm orders (`weight_before_norm` true and
false). No Cake version of this collective shipped on sm_107a before, so
the table below compares Cake with FlashInfer's existing CuTe DSL
kernels (PR #6544). Both sides run through the same public API on the
same node in the same processes. The table covers the BF16,
`weight_before_norm=True` variant at TP4. T is the token count, and
speedup = baseline µs / Cake µs. Cake is faster at every T, from 1.014
at T = 31 to 3.873 at T = 8192.

**TP4 on NVIDIA R200 (`sm_107a`, 212 SMs), CUDA 13.0** (slowest rank,
isolated launch, cold L2, BF16 routing weights, weight before the norm)

| T | baseline µs | Cake µs | speedup |
|---|---|---|---|
| 1 | 9.75 | 8.61 | 1.133 |
| 4 | 10.66 | 9.07 | 1.175 |
| 8 | 10.97 | 9.62 | 1.140 |
| 15 | 11.42 | 11.14 | 1.026 |
| 16 | 12.46 | 11.26 | 1.107 |
| 17 | 12.48 | 11.23 | 1.111 |
| 24 | 12.88 | 11.70 | 1.100 |
| 31 | 12.63 | 12.46 | 1.014 |
| 32 | 14.51 | 12.10 | 1.199 |
| 33 | 14.31 | 12.52 | 1.143 |
| 36 | 14.38 | 12.62 | 1.139 |
| 48 | 14.40 | 13.56 | 1.062 |
| 49 | 14.76 | 13.81 | 1.069 |
| 53 | 15.74 | 13.85 | 1.137 |
| 64 | 16.36 | 14.35 | 1.140 |
| 76 | 16.96 | 15.17 | 1.118 |
| 106 | 19.30 | 16.71 | 1.155 |
| 128 | 20.19 | 17.86 | 1.131 |
| 148 | 21.14 | 18.59 | 1.137 |
| 152 | 21.38 | 18.79 | 1.138 |
| 153 | 21.54 | 18.79 | 1.146 |
| 212 | 24.48 | 21.67 | 1.130 |
| 213 | 44.98 | 28.37 | 1.585 |
| 256 | 53.35 | 30.66 | 1.740 |
| 512 | 104.83 | 43.05 | 2.435 |
| 1024 | 211.24 | 70.12 | 3.013 |
| 2048 | 422.50 | 123.98 | 3.408 |
| 4096 | 844.93 | 227.15 | 3.720 |
| 8192 | 1691.35 | 436.65 | 3.873 |

Besides the variant timed above, the package also serves FP32
`expert_weights`, `weight_before_norm=False` and TP2 on the Blackwell
architectures; it ships on sm_100a (TP2, TP8), sm_103a (TP2, TP4) and,
with this PR, sm_107a (TP4), and does not route sm_100a TP4, sm_103a
TP8, or sm_107a TP2 / TP8.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for SM107 GPUs for select tensor-parallel MoE
configurations.
* Expanded available kernel variants and routing options for supported
GPU architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6bb12ce](https://github.com/flashinfer-ai/flashinfer/commit/6bb12ce183488e47da8defc8276bf74b6c909f7a)

- **作者**: eigen
- **时间**: 2026-10-24T11:43:51Z
- **提交信息**: deslop(cake_deepseek_fused_routing): drop the 117 explicit kernel instantiations (#7172)

## 📌 Description

### Summary

The DeepSeek fused-routing kernels (`fused_topk_deepseek`, backend
`cake`) are Cake-generated CUDA under
`csrc/fused_moe/cake_deepseek_fused_routing/`. Each of the three kernel
files ends with a block of explicit instantiation directives. There are
117 directives in all. They are redundant, because the launcher already
instantiates every kernel they name in the same translation unit. This
PR deletes the three blocks. It is a pure deletion of 274 lines.

The Validation rows compare the base with the head. Preprocessed text
must equal the base text minus the deleted lines. SASS, symbol tables,
resource usage, kernel metadata and host exports must be identical. Test
outcomes must be identical per id.

### Source layout

Base: `main` `c7c821c2a`. Head: d4d1c8792a81886ab6781c32d09e952abc282f42
(1 commit).

The exporter folded the original kernels into kernel templates. It
instantiated them for the nine (scores, bias) dtype pairs of {fp32,
fp16, bf16}. The three kernel files are:
- `cake_deepseek_fused_routing_kernels.cu` holds two templates for SM100
and SM103. It also holds the generic path on SM107. The first template
is `kernel_cake_deepseek_routing_grouped<ScoreT, BiasT,
kGroupRankUnroll, kRouteUnroll>`, used as `<1, 1>` and `<4, 8>`. The
second is `kernel_cake_deepseek_routing_single<ScoreT, BiasT,
kThreads>`, used as `<128>` and `<384>`.
- `cake_deepseek_fused_routing_kernels_sm107a_single.cu` holds the SM107
single-group members (namespace `cake_deepseek_routing_sm107a_single`).
- `cake_deepseek_fused_routing_kernels_sm107a_mt.cu` holds the SM107
multi-token members `kernel_cake_deepseek_routing_grouped_k8g4_mt2` ..
`mt8` (namespace `cake_deepseek_routing_sm107a_mt`).

`csrc/fused_moe/noAuxTcKernels.cu` includes all three files (lines
13-15). The launcher header
`csrc/fused_moe/cake_deepseek_fused_routing_launch.cuh` follows at line
16. Together they form one translation unit. The JIT module is
`dsv3_fused_routing_cake` (`flashinfer/jit/dsv3_optimizations.py`).

### Commit 1 (d4d1c8792) - cake_deepseek_fused_routing: drop the
explicit kernel instantiations

3 files changed: 0 insertions, 274 deletions.

- **Removed blocks.** Each kernel file ended with a block headed by this
comment: `// One explicit instantiation per original kernel (schedule x
score/bias dtype pair).` In each file, the commit removes that comment
line and the directives after it. The removal stops at the blank line
before `#undef CAKE_INF`. No other line changes.
- `cake_deepseek_fused_routing_kernels.cu`: 36 directives (4 x 9). The 4
are `grouped<1, 1>`, `grouped<4, 8>`, `single<128>` and `single<384>`,
for each of the nine pairs. 78 lines go (518 -> 440).
- `cake_deepseek_fused_routing_kernels_sm107a_single.cu`: 18 directives
(2 x 9), the two single-group members for each pair. 40 lines go (208 ->
168).
- `cake_deepseek_fused_routing_kernels_sm107a_mt.cu`: 63 directives (7 x
9), `mt2` .. `mt8` for each pair. 156 lines go (2,840 -> 2,684).

  In all, 117 directives and 274 lines (78 + 40 + 156) go.
- **Why the directives are redundant.** `launch<ScoreT, BiasT>` in the
launcher header passes every one of these specializations to
`cudaLaunchKernelEx`. These are:
  - `grouped<.., 4, 8>` and `grouped<.., 1, 1>`;
  - `single<.., 128>` and `single<.., 384>`;
  - the two SM107 single-group members;
  - the seven multi-token members.

`NoAuxTc` in `noAuxTcKernels.cu` switches on the two dtypes. It calls
`invokeNoAuxTc`, and through it `launch<>`, for all nine (scores, bias)
pairs. Taking the address of a function template specialization
instantiates it. So every kernel that a directive names is already
instantiated implicitly. This happens in the same translation unit, in
every device pass.
- **No other user.** Only the three kernel files and the launcher header
name the kernel templates. No other source includes the kernel files.
- **Generated file.** The kernel files carry the exporter's "Generated
file; do not edit manually" marker. This commit is a hand edit of
generated text. The exporter should stop emitting the directives at the
next regeneration. That change is listed under "Not in this PR".
- **Behaviour.** Behaviour is unchanged for every input. The module
holds the same kernels with the same code. The host dispatch is
untouched.

### Validation

All rows compare the base tree (`main` `c7c821c2a`) with the branch head
d4d1c8792a81886ab6781c32d09e952abc282f42. Both sides use the same `nvcc`
and the same flag line.

- **Preprocessed text.** Both `nvcc -E` passes (device and host) of
`csrc/fused_moe/noAuxTcKernels.cu` ran on `sm_100a`, `sm_103a`,
`sm_107a` and `sm_100f`. The head text must equal the base text minus
exactly the deleted lines. The line markers of the three kernel files
shift by the deleted counts: both -E passes (device and host) on 4
arches: the candidate text equals the base text minus exactly the 274
deleted lines (cake_deepseek_fused_routing_kernels.cu 76,
cake_deepseek_fused_routing_kernels_sm107a_single.cu 38,
cake_deepseek_fused_routing_kernels_sm107a_mt.cu 154 non-blank directive
lines dropped), the kernel files' line markers shifted by the deleted
counts, nothing else
- **Untouched co-sources.** The other sources of the JIT module are the
launcher header and the host sources. They must be blob-identical: 9/9
untouched co-sources (the module's other sources, the launcher header,
the direct includes) blob-identical
- **SASS.** `nvcc -cubin` builds the unit per arch. `cuobjdump -sass`
output is compared per kernel function, with labels canonicalised. Every
kernel must be identical. The function set must be identical, with no
kernel added or removed: 4/4 (117 kernel functions identical per
function block on sm_100a, sm_103a, sm_107a and sm_100f; the function
set identical; CUDA 13.4; flag line derived from the JIT build recipe,
not captured)
- **Symbol tables.** The full `cuobjdump -symbols` table (type, binding,
name) must be identical per arch. One compiler-internal module id is
masked on both sides: 4/4 (full symbol tables identical after the
module-id canonicalisation; 0 removed / 0 added entries)
- **Resource usage and kernel metadata.** `cuobjdump -res-usage` output
and the decoded per-kernel `.nv.info` records must be identical: RES
4/4, .nv.info 4/4 identical per kernel (117/117 decoded on 100a)
- **Host object.** The `nvcc -c` host object must export the same
defined symbols (`nm`). It must hold the same undefined references: 4/4
(defined and undefined host symbols identical after the module-id
canonicalisation; the entry export present on both sides)
- **References.** The kernel template names and the kernel file names
may appear only in five files. These are the three kernel files, the
launcher header and the translation unit. The base must show the same
set: 8/8 (the 3 kernel template names, the 3 kernel file names, the
launcher name and the family name are referenced only by the allowed
five files, identically at the base)
- **Flag line.** The compile flag line of record comes from the JIT
build recipe of `dsv3_fused_routing_cake`: derived from the JIT build
recipe on sm_100a, sm_103a, sm_107a, sm_100f, not captured
- **Apply replay.** The data-driven deletion script is re-applied on a
fresh base checkout. The result must equal the branch tree: the U1 apply
script (--check-only, then apply) re-run on a fresh worktree of the
base; tree byte-identical to the commit
- **Tests on B200 (SM100).**
`tests/model_optimizations/test_dsv3_fused_routing.py` and
`tests/model_optimizations/test_dsv3_fused_routing_backend_selection.py`
run in full on both trees. Each tree uses a fresh JIT cache. Every id
must have the same outcome on both trees, skip reasons included: 5500
ids over the two files on B200 (sm_100a) (driver 580.82.07, CUDA 13.3):
1144 passed / 4356 skipped, per-id identical on both trees incl. skip
reasons; fresh JIT workspace per arm (2 cuda_compile + 4 c++ edges of
the module, module dir absent before each arm); TF32 override off
- **Tests on GB300 (SM103).** The same two files, with the same
protocol: 5500 ids over the two files on GB300 (sm_103a) (driver
580.167.08, CUDA 13.3): 1144 passed / 4356 skipped, per-id identical on
both trees incl. skip reasons; fresh JIT workspace per arm (2
cuda_compile + 4 c++ edges of the module, module dir absent before each
arm); TF32 override off
- **Tests on R200 (SM107).** The same two files, with the same protocol.
The `sm_107a` and `sm_100f` identity rows above are the SM107 evidence
either way. `sm_100f` is the family target that the JIT builds for
compute capability 10.7 devices. Whether an R200 run happened, and its
result: the R200 test row (SM107) was not run: no R200 runner was
available; the sm_107a identity proof is the compile-only rows of the
gate step (preprocessed text, SASS, symbol tables, resource usage,
kernel metadata and the host object)
- **CPU-only run.** On both trees: collect-only parity of the two files,
and the host-only ids of the backend-selection file: 5500 ids collected
on both trees over the two files (CUDA hidden); the backend-selection
file ran per id on both trees: 49 ids, 49 passed on both arms (every
base-passed id passes on the candidate), 0 skipped; per-id identical
- **Static checks.** The checks cover the chain shape, a pure-deletion
diff, and the files this PR must not touch. They also cover source
hygiene, pre-commit on the three files (clang-format applies to them)
and a public-text scan: 11/11
- **Rows not run.** Planned rows that did not run: 2 (the flag-line row
(the JIT build's compile line was not captured; see that row); the R200
test row (no R200 runner was available; see that row))

### Not in this PR

- The exporter-side change that stops emitting the directives. Until it
lands, a re-export would re-emit them.
- The `INSTANTIATE_NOAUX_TC` block under `#ifdef ENABLE_BF16` in
`csrc/fused_moe/noAuxTcKernels.cu`. It is host code of the original
backend, not generated by Cake.
- The `cake_rmsnorm_train` items of #6680. That package is being
re-exported for #7045, and these items wait for the re-export.
- Shared files this PR never edits: `csrc/fused_moe/noAuxTcKernels.cu`,
`csrc/fused_moe/cake_deepseek_fused_routing_launch.cuh`,
`flashinfer/jit/dsv3_optimizations.py`, the tests,
`.pre-commit-config.yaml`, `pyproject.toml`, `.github/**`, `scripts/**`.

## 🔍 Related Issues

Part of #6680

#6680 is the round-2 deslop family issue. Its round-2 PR #7122 covered
the softmax package. The issue's final comment lists this deletion as a
possible follow-up.

## 🚀 Pull Request Checklist

I have read the contributing guide. The three changed files are
formatted, and pre-commit ran on them.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks ran on the three changed files and pass on both trees.
clang-format applies to these files. The Static checks row in Validation
gives the result.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

No test file changes. The PR deletes only redundant directives, so no
test change is needed. The two fused-routing test files ran on B200 and
GB300, on both trees. The R200 row states whether an R200 run happened.
The test rows in Validation give the per-id outcomes. The criterion is
identical outcomes on both trees.

## 🔬 Experimental Track

`cake_deepseek_fused_routing` is not an experimental-track package. This
PR declares no experimental test target.

```experimental-tests
```

## Reviewer Notes

- **Base.** The identity rows were compiled at `main` c7c821c2a; the
static rebase check ran versus `main` 8eccdc880 (no file of this PR
changed in between).
- **Toolkit.** The identity rows ran on a CPU node with the same toolkit
on both sides.
- **#7111.** Open PR #7111 edits line 164 of
`cake_deepseek_fused_routing_kernels.cu` (a group-index initial value),
and the block deleted here starts at line 440, so the hunks do not
overlap and either merge order is conflict-free.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Updated the compiled routing-kernel variants. Public interfaces and
kernel implementations remain unchanged.
  * No end-user-facing behavior changes are described.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bd7f082](https://github.com/flashinfer-ai/flashinfer/commit/bd7f082ae896e32d4044f0224bc5624c022ee17e)

- **作者**: Yang Xu
- **时间**: 2026-10-24T10:31:04Z
- **提交信息**: feat(moe): add E4M3 weight-only BF16 activation to Frost (#7166)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add E4M3 weight-only MoE to `frost_low_latency`: `weight=FP8PerTensor,
activation=BF16`, with BF16 output. It reuses the existing routed FMA
pipeline and compiled FFI binding, preserving checkpoint E4M3 bytes and
live per-expert FP32 dequantization scales while avoiding activation
quantization. All ten typed activations are supported. Default backend
selection is unchanged.

The change adds byte-preserving weight preparation, independent
activation/weight load types in the shared FMA kernels, cache-key dtype
separation, 23 GPU contract tests, and a reproducible native comparison.

H=2048/I=512/E=512/top-k=10, SwiGLU, full routed-expert GPU time in
microseconds:

| GPU | T / routes / cache | Tuned cuTile | Frost | Speedup |
|---|---|---:|---:|---:|
| RTX PRO 6000 Blackwell (SM120) | T1 warm | 18.912 | 8.608 | 2.20× |
| RTX PRO 6000 Blackwell (SM120) | T1 cold | 37.288 | 26.143 | 1.43× |
| RTX PRO 6000 Blackwell (SM120) | T2 disjoint warm | 60.831 | 13.248 |
4.59× |
| RTX PRO 6000 Blackwell (SM120) | T8 shared warm | 28.816 | 38.088 |
0.76× |
| H100 (SM90) | T1 warm | 33.600 | 11.920 | 2.82× |
| H100 (SM90) | T1 cold | 42.864 | 22.328 | 1.92× |
| H100 (SM90) | T8 shared warm | 43.072 | 46.632 | 0.92× |

These are same-GPU, same-shape/cache/routing, matched-rounding kernel
comparisons, not model throughput. The T8/shared losses are retained:
larger expert reuse can favor Tensor Cores. Native selection tests all
advertised stage pairs for all supported blocks and gather/sorted modes
plus default (289–351 candidates for these cases); Frost tests 16 column
pairs. Four frozen ABBA rounds and independent warm event-chain controls
follow selection. CUPTI spans include all required GPU work; cold
eviction and host enqueue are excluded. Full provenance and samples:
`docs/frost_low_latency_w8a16.json`; reproducer:
`benchmarks/bench_frost_low_latency_w8a16.py`.

## 🔍 Related Issues

Builds on #7162 (ordinary FP8 and SM90) and #7153 (FP16 and SM120).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Scoped `pre-commit run --files ...` and `git diff --check` pass for all
changed files; a repository-wide formatting sweep was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

The 23 new tests pass on SM120, SM103 and SM90. They cover typed
activations, dynamic scales/routes and graph replay, invalid IDs,
packed/unpacked routing, raw/final output, exact payload/padding,
nondefault Torch dtype, T8/top-k32 column extremes, and fresh-buffer
cache rebinding after W8A8 compilation. Earlier consolidated eight-file
suites (19 new tests at that revision) passed SM120 194/45 skipped,
SM103 236/3, and SM90 128/111; the final four max-route checks then
passed separately. Native SM100/SM107 qualification is pending CI; this
is not a claim that every repository test ran.

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

- BF16-only activation/output for this new pair. FC1 rounds
preactivation and intermediate to BF16; FC2 rounds each expert result to
BF16 before ordered FP32 combination. Packed scores retain BF16
rounding.
- Preparation scales are weight-only calibration, not the W8A8 helper's
folded input/intermediate scales. The shared ABI's unused intermediate
quantization field is poisoned in a test to ensure it is not read.
- No new architecture-specific instructions or separate FMA kernel body.
The compiled cache includes input/intermediate dtypes so W8A8 and W8A16
cannot alias.
- Benchmark stage-ranking hooks receive private routing copies; actual
measured routing is saved and checked unchanged. Large-tensor native
compiler workarounds remain outside this PR and outside its performance
claims.
- AI-assisted implementation and validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added opt-in Frost low-latency inference with E4M3 (FP8) weights, BF16
activations, and per-expert FP32 weight scales.
* Added weight preparation for this mode, including padding for
compatible workloads.
* Expanded supported Frost low-latency quantization combinations and
added a benchmark comparing Frost with native cuTile.
* **Documentation**
* Documented supported inputs, execution behavior, and benchmark
results, including cases where Frost is slower than cuTile.
* **Bug Fixes**
* Improved handling of FP8 weights with BF16 inputs and intermediate
values.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1ed08fc](https://github.com/flashinfer-ai/flashinfer/commit/1ed08fc2ccff810384f2abb25443f935cc22fcd3)

- **作者**: eigen
- **时间**: 2026-10-24T10:28:58Z
- **提交信息**: perf(cake_gdp): read the split-V T = 1 state cells straight into registers on SM100 / SM103 (#7156)

The Cake Gated DeltaProduct decode kernel
(`flashinfer.cake_gdp.cake_gated_delta_product_mtp`) has one variant:
BF16 q / k / v / output with an FP32 recurrent state in a slot-indexed
state pool, float32 `A_log` and `dt_bias`, optional per-token state
scatter, 1 <= T <= 16 tokens per sequence, K = 128, V = 64 and 1 <= n <=
4 Householder sub-steps. This PR delivers that same variant with a
change inside one T = 1 kernel on sm_100a / sm_103a, the split-V kernel
that serves the smallest B x HV rows by splitting the V dimension across
the CTA: each thread now reads its recurrent-state cells straight from
the state pool into registers with two 128-bit global loads, the
shared-memory staging of those cells and its group wait are removed, and
the kernel's dynamic shared memory drops from 6400 to 2304 bytes. The
cells, the operands and their order are unchanged, so outputs and state
writes are bitwise equal to the previous package, and the host plan,
kernel selection rule and public API are unchanged; exactly two compiled
kernel entries change (this kernel for sm_100a and sm_103a), and the
other 41, including every sm_90a kernel, the one-head and
two-heads-per-CTA T = 1 kernels and the T = 4 / T = 8 kernels, are
machine-code-identical to the previous package. The baseline is the
previous Cake version of this kernel, the Cake GDP decode package merged
in FlashInfer PR #7138 (now on main, the direct predecessor of this
package); both packages ran in the same process on the same GPU with the
same inputs, interleaved A B B A over 3 groups x 32 samples per call,
with cold L2 and kernel time measured, and speedup = previous / this PR
is 0.98-1.04 on GB300 and 0.99-1.06 on B200 across the 48 shapes (HV in
{80, 20, 10, 24} x B in {1, 16, 64, 256} x T in {1, 4, 8}, n = 3). The
changed kernel runs on the five T = 1 split-V rows (every B = 1 row and
HV 10 / B 16), where the speedup is 1.00-1.04 on GB300 and 1.01-1.06 on
B200; all other rows run unchanged kernels.

**NVIDIA GB300 (sm_103a), CUDA 13.4.92 -- 48 rows, speedup 0.98-1.04**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.2 | 4.1 | 1.03 |
| 80 | 1 | 4 | 6.0 | 6.1 | 0.99 |
| 80 | 1 | 8 | 8.2 | 8.1 | 1.01 |
| 80 | 16 | 1 | 17.5 | 18.0 | 0.98 |
| 80 | 16 | 4 | 24.8 | 24.7 | 1.01 |
| 80 | 16 | 8 | 40.1 | 40.0 | 1.00 |
| 80 | 64 | 1 | 55.0 | 55.0 | 1.00 |
| 80 | 64 | 4 | 76.0 | 76.0 | 1.00 |
| 80 | 64 | 8 | 131.3 | 131.4 | 1.00 |
| 80 | 256 | 1 | 198.9 | 199.4 | 1.00 |
| 80 | 256 | 4 | 281.8 | 281.8 | 1.00 |
| 80 | 256 | 8 | 499.5 | 499.5 | 1.00 |
| 20 | 1 | 1 | 3.3 | 3.3 | 1.00 |
| 20 | 1 | 4 | 5.6 | 5.6 | 1.00 |
| 20 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 20 | 16 | 1 | 7.4 | 7.4 | 1.00 |
| 20 | 16 | 4 | 10.9 | 11.0 | 0.99 |
| 20 | 16 | 8 | 16.6 | 16.7 | 1.00 |
| 20 | 64 | 1 | 17.7 | 17.3 | 1.02 |
| 20 | 64 | 4 | 24.5 | 24.5 | 1.00 |
| 20 | 64 | 8 | 40.0 | 40.0 | 1.00 |
| 20 | 256 | 1 | 55.2 | 55.2 | 1.00 |
| 20 | 256 | 4 | 76.0 | 76.1 | 1.00 |
| 20 | 256 | 8 | 131.5 | 131.4 | 1.00 |
| 10 | 1 | 1 | 3.2 | 3.2 | 1.00 |
| 10 | 1 | 4 | 5.5 | 5.5 | 1.00 |
| 10 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 10 | 16 | 1 | 5.2 | 5.0 | 1.04 |
| 10 | 16 | 4 | 8.3 | 8.2 | 1.01 |
| 10 | 16 | 8 | 11.9 | 12.0 | 0.99 |
| 10 | 64 | 1 | 11.1 | 11.1 | 1.00 |
| 10 | 64 | 4 | 15.9 | 16.0 | 1.00 |
| 10 | 64 | 8 | 24.9 | 25.2 | 0.99 |
| 10 | 256 | 1 | 30.0 | 30.3 | 0.99 |
| 10 | 256 | 4 | 41.4 | 41.5 | 1.00 |
| 10 | 256 | 8 | 69.5 | 69.6 | 1.00 |
| 24 | 1 | 1 | 3.3 | 3.3 | 1.00 |
| 24 | 1 | 4 | 5.6 | 5.6 | 1.00 |
| 24 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 24 | 16 | 1 | 7.8 | 7.9 | 1.00 |
| 24 | 16 | 4 | 11.4 | 11.4 | 1.01 |
| 24 | 16 | 8 | 17.2 | 17.2 | 1.00 |
| 24 | 64 | 1 | 20.4 | 19.9 | 1.03 |
| 24 | 64 | 4 | 28.2 | 28.4 | 0.99 |
| 24 | 64 | 8 | 46.9 | 47.0 | 1.00 |
| 24 | 256 | 1 | 64.6 | 64.9 | 0.99 |
| 24 | 256 | 4 | 90.0 | 90.0 | 1.00 |
| 24 | 256 | 8 | 156.3 | 156.3 | 1.00 |

**NVIDIA B200 (sm_100a), CUDA 13.4.92 -- 48 rows, speedup 0.99-1.06**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.3 | 4.3 | 1.02 |
| 80 | 1 | 4 | 6.3 | 6.4 | 0.99 |
| 80 | 1 | 8 | 8.6 | 8.6 | 1.00 |
| 80 | 16 | 1 | 18.8 | 18.4 | 1.02 |
| 80 | 16 | 4 | 26.4 | 26.6 | 0.99 |
| 80 | 16 | 8 | 43.5 | 43.6 | 1.00 |
| 80 | 64 | 1 | 57.3 | 57.5 | 1.00 |
| 80 | 64 | 4 | 83.2 | 83.1 | 1.00 |
| 80 | 64 | 8 | 144.7 | 144.7 | 1.00 |
| 80 | 256 | 1 | 205.7 | 205.4 | 1.00 |
| 80 | 256 | 4 | 306.0 | 305.9 | 1.00 |
| 80 | 256 | 8 | 543.6 | 543.7 | 1.00 |
| 20 | 1 | 1 | 3.4 | 3.4 | 1.01 |
| 20 | 1 | 4 | 5.8 | 5.8 | 0.99 |
| 20 | 1 | 8 | 8.1 | 8.1 | 1.00 |
| 20 | 16 | 1 | 7.8 | 7.8 | 1.00 |
| 20 | 16 | 4 | 11.6 | 11.6 | 1.00 |
| 20 | 16 | 8 | 17.8 | 17.8 | 1.00 |
| 20 | 64 | 1 | 18.5 | 18.5 | 1.00 |
| 20 | 64 | 4 | 26.5 | 26.7 | 0.99 |
| 20 | 64 | 8 | 43.5 | 43.6 | 1.00 |
| 20 | 256 | 1 | 57.4 | 57.5 | 1.00 |
| 20 | 256 | 4 | 83.2 | 83.3 | 1.00 |
| 20 | 256 | 8 | 144.9 | 144.8 | 1.00 |
| 10 | 1 | 1 | 3.3 | 3.3 | 1.02 |
| 10 | 1 | 4 | 5.7 | 5.7 | 0.99 |
| 10 | 1 | 8 | 8.0 | 8.0 | 1.00 |
| 10 | 16 | 1 | 5.5 | 5.2 | 1.06 |
| 10 | 16 | 4 | 8.6 | 8.5 | 1.01 |
| 10 | 16 | 8 | 12.9 | 12.7 | 1.01 |
| 10 | 64 | 1 | 11.8 | 11.7 | 1.00 |
| 10 | 64 | 4 | 16.8 | 17.0 | 0.99 |
| 10 | 64 | 8 | 27.3 | 27.3 | 1.00 |
| 10 | 256 | 1 | 31.6 | 31.5 | 1.00 |
| 10 | 256 | 4 | 45.8 | 45.8 | 1.00 |
| 10 | 256 | 8 | 78.3 | 78.3 | 1.00 |
| 24 | 1 | 1 | 3.5 | 3.5 | 1.01 |
| 24 | 1 | 4 | 5.9 | 5.8 | 1.01 |
| 24 | 1 | 8 | 8.1 | 8.1 | 1.00 |
| 24 | 16 | 1 | 8.2 | 8.3 | 0.99 |
| 24 | 16 | 4 | 12.1 | 12.2 | 0.99 |
| 24 | 16 | 8 | 18.4 | 18.4 | 1.00 |
| 24 | 64 | 1 | 21.6 | 21.0 | 1.03 |
| 24 | 64 | 4 | 30.5 | 30.5 | 1.00 |
| 24 | 64 | 8 | 51.2 | 51.2 | 1.00 |
| 24 | 256 | 1 | 67.2 | 67.2 | 1.00 |
| 24 | 256 | 4 | 98.2 | 98.6 | 1.00 |
| 24 | 256 | 8 | 171.7 | 171.6 | 1.00 |

This variant is the kernel family's only data-type form; Cake ships it
on sm_90a (H100 / H200), sm_100a (B200 / GB200) and sm_103a (B300 /
GB300), and this PR changes two sm_100a / sm_103a kernels (the T = 1
split-V program) and adds none.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Reduced shared-memory requirements for the affected GPU decode
operation, from 6,400 bytes to 2,304 bytes. This changes how the
operation uses GPU resources while preserving its existing output and
state-update behavior.
* Updated the associated build metadata to match the revised
implementation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>

### [5d699c5](https://github.com/flashinfer-ai/flashinfer/commit/5d699c5cabe55d116b7f2a0831c518045abba793)

- **作者**: Yang Xu
- **时间**: 2026-10-24T10:28:08Z
- **提交信息**: fix(moe): preserve valid loop bounds for cuTile wide indexing (#7168)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix sorted cuTile FP8/MX MoE compilation when large expert tensors
select 64-bit indexing. `IndexedWithInt64` makes the tensor-shape K loop
bound int64 while tileiras constructs an int32 induction variable,
causing `cuda_tile.for` verification to reject mismatched
lower/upper/step types.

Pass the model K as a compile-time scalar for wide-index sorted GEMMs,
including fused MX GEMM1. Ordinary indexing keeps the existing
tensor-shape bound and specialization; all pointer/index arithmetic
stays unchanged. Add forced-wide small-allocation tests with bitwise
narrow/wide comparison and changed routing weights under CUDA Graph
replay.

## 🔍 Related Issues

Discovered while qualifying the native cuTile baseline for #7166. This
fix is independent of Frost and does not change the stock-baseline
records in that PR.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Scoped hooks passed for both changed files; repository-wide formatting
was intentionally not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation (repository-wide CI pending):
- Original H100 forced-wide reproducer fails with the loop-bound type
mismatch; repaired native paths execute correctly.
- RTX PRO 6000 Blackwell Workstation (SM120): 15 targeted tests passed.
- H100 (SM90): 8 passed / 5 skipped for unsupported native format
combinations.
- New regression: `pytest -q
tests/moe/test_cutile_fp8_wide_indexing.py`.
- Existing sorted execution / graph / int64 guards were also included.
- Eight fixed-tactic normal-index CUPTI controls are bitwise equal. At
H2048/I512, W8A16 T1 is 19.040 → 19.040 µs and T8 is 25.224 → 25.248 µs.
Across ordinary FP8 and MX modes, original/fixed ratios are
0.994916–1.001765 (within 0.6%). These are regression controls, not a
speedup claim.

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

The zero K sentinel preserves the normal-index compiler specialization.
Always-static-K and 64-bit while-loop alternatives changed normal-path
scheduling and were rejected after measurement. No numerical tolerance
or architecture guard was relaxed. The small-allocation forced-wide
regression avoids requiring multi-GiB weights in every CI worker.
AI-assisted implementation and validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved FP8 and MX grouped GEMM handling for wide-indexed inputs,
helping ensure results remain consistent across indexing modes.
* Corrected tile-count handling for model input widths, supporting
reliable execution across normal and wide-indexed calls.
* Added coverage for CUDA graph replay to verify that outputs remain
consistent after replay with scaled inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8eccdc8](https://github.com/flashinfer-ai/flashinfer/commit/8eccdc8806257ccf43c85e546b8a8f9a6c95355c)

- **作者**: eigen
- **时间**: 2026-10-24T10:14:02Z
- **提交信息**: perf(cake_dsa_indexer): far_sample scan scalar, predicated slot reservation and per-program register-usage flags (#7171)

This PR tunes the Cake DSA indexer top-k scan behind
`flashinfer.dsa_indexer.dsa_indexer_topk`, which has only one data-type
variant (BF16 queries and keys, FP32 head weights and scores). It also
adds a `far_sample` option, which is off by default on every
architecture. Both kernels were measured with the default plan. Against
the previous Cake version of this kernel in FlashInfer main, the speedup
is 1.00x–1.02x on all 29 GB300 rows and 1.00x–1.04x on all 29 GB200
rows, with bit-identical output. Turning on `far_sample=1` is a trade.
It is faster on GB300 attention-sink rows (up to 1.35x on Z1k4096) and
slower on the Z2/Z3 rows (down to 0.82x on GB300 Z2cp and 0.93x on GB200
Z3cp), so the default stays 0. The tables measure the default plan and,
in two extra columns, `far_sample=1`.

Speedup on GB200:

GB200 (NVIDIA GB200, sm_100a, CUDA 13.4 (nvcc 13.4.92)); ms = median of
the two arm-order processes of the CUPTI kernel time; speedup = previous
/ this PR; the far_sample=1 columns time the same package with the
option on. Rows Z1k4096, S4, C2 and V2 are the median of three arm-order
processes.

| row | shape | T (queries) | Tkv (keys) | segments | top-k | previous
Cake kernel ms | this PR ms (default) | speedup | this PR ms
(far_sample=1) | speedup |
|---|---|---|---|---|---|---|---|---|---|---|
| Z1 | #7042 repro: 262k document, CP16 zigzag rank 0 | 16384 | 270336 |
2 | 2048 | 12.897 | 12.731 | 1.01x | 12.764 | 1.01x |
| Z1k4096 | Z1 with top-k 4096 | 16384 | 270336 | 2 | 4096 | 13.613 |
13.432 | 1.01x | 13.458 | 1.01x |
| Z1k256 | Z1 with top-k 256 | 16384 | 270336 | 2 | 256 | 12.774 |
12.560 | 1.02x | 12.630 | 1.01x |
| Z2 | 8 x 32k documents, full causal | 262144 | 262144 | 8 | 2048 |
34.421 | 33.653 | 1.02x | 33.709 | 1.02x |
| Z2cp | 8 x 32k documents, CP16 zigzag rank 0 | 16384 | 270336 | 16 |
2048 | 2.253 | 2.209 | 1.02x | 2.212 | 1.02x |
| Z3 | packed 4k-64k documents, full causal | 169984 | 169984 | 8 | 2048
| 24.548 | 24.632 | 1.00x | 25.605 | 0.96x |
| Z3cp | packed 4k-64k documents, CP16 zigzag rank 0 | 10624 | 175296 |
16 | 2048 | 1.662 | 1.661 | 1.00x | 1.792 | 0.93x |
| P1sink | recorded P1 geometry with sink statistics | 16231 | 268757 |
8 | 2048 | 3.421 | 3.384 | 1.01x | 3.370 | 1.02x |
| S4sink | one 64k causal document, sink statistics | 65536 | 65536 | 1
| 2048 | 14.699 | 14.528 | 1.01x | 14.635 | 1.00x |
| S6sink | one 262k causal document, sink statistics | 262144 | 262144 |
1 | 2048 | 213.627 | 210.635 | 1.01x | 210.812 | 1.01x |
| P1 | recorded packed call | 16231 | 268757 | 8 | 2048 | 3.537 | 3.467
| 1.02x | 3.474 | 1.02x |
| P1_peaked | P1 with dominating keys | 16231 | 268757 | 8 | 2048 |
3.561 | 3.492 | 1.02x | 3.491 | 1.02x |
| P2 | second recorded token count, boundaries derived | 16172 | 267520
| 8 | 2048 | 3.570 | 3.492 | 1.02x | 3.533 | 1.01x |
| P3 | P1 with top-k 4096 | 16231 | 268757 | 8 | 4096 | 3.832 | 3.761 |
1.02x | 3.771 | 1.02x |
| S1 | single causal document N = 8192 | 8192 | 8192 | 1 | 2048 | 0.426
| 0.426 | 1.00x | 0.429 | 0.99x |
| S2 | single causal document N = 16384 | 16384 | 16384 | 1 | 2048 |
1.224 | 1.225 | 1.00x | 1.236 | 0.99x |
| S3 | single causal document N = 32768 | 32768 | 32768 | 1 | 2048 |
4.053 | 3.899 | 1.04x | 3.910 | 1.04x |
| S4 | single causal document N = 65536 | 65536 | 65536 | 1 | 2048 |
14.491 | 14.308 | 1.01x | 14.318 | 1.01x |
| S5 | single causal document N = 131072 | 131072 | 131072 | 1 | 2048 |
55.284 | 55.161 | 1.00x | 54.863 | 1.01x |
| S6 | single causal document N = 262144 | 262144 | 262144 | 1 | 2048 |
215.115 | 213.640 | 1.01x | 213.756 | 1.01x |
| S7 | single causal document N = 524288 | 524288 | 524288 | 1 | 2048 |
878.949 | 872.572 | 1.01x | 871.790 | 1.01x |
| S4_peaked | S4 with dominating keys | 65536 | 65536 | 1 | 2048 |
14.628 | 14.346 | 1.02x | 14.507 | 1.01x |
| C1 | CP tail 4096 x 65536 | 4096 | 65536 | 1 | 2048 | 1.697 | 1.694 |
1.00x | 1.693 | 1.00x |
| C2 | CP tail 4096 x 131072 | 4096 | 131072 | 1 | 2048 | 3.217 | 3.183
| 1.01x | 3.203 | 1.00x |
| C3 | packed 8 x (2048 x 32768) | 16384 | 262144 | 8 | 2048 | 3.476 |
3.354 | 1.04x | 3.351 | 1.04x |
| V1 | N = 65536, ratio 2 | 65536 | 32768 | 1 | 2048 | 8.195 | 8.028 |
1.02x | 8.010 | 1.02x |
| V2 | N = 65536, top-k 256 | 65536 | 65536 | 1 | 256 | 13.305 | 13.133
| 1.01x | 13.279 | 1.00x |
| V3 | N = 65536, top-k 4096 | 65536 | 65536 | 1 | 4096 | 15.583 |
15.536 | 1.00x | 15.511 | 1.00x |
| S8 | single causal document N = 1048576 | 1048576 | 1048576 | 1 | 2048
| 3792.602 | 3753.528 | 1.01x | 3759.721 | 1.01x |

Speedup on GB300:

GB300 (NVIDIA GB300, sm_103a, CUDA 13.4 (nvcc 13.4.92)); ms = median of
the two arm-order processes of the CUPTI kernel time; speedup = previous
/ this PR; the far_sample=1 columns time the same package with the
option on.

| row | shape | T (queries) | Tkv (keys) | segments | top-k | previous
Cake kernel ms | this PR ms (default) | speedup | this PR ms
(far_sample=1) | speedup |
|---|---|---|---|---|---|---|---|---|---|---|
| Z1 | #7042 repro: 262k document, CP16 zigzag rank 0 | 16384 | 270336 |
2 | 2048 | 12.103 | 12.072 | 1.00x | 11.410 | 1.06x |
| Z1k4096 | Z1 with top-k 4096 | 16384 | 270336 | 2 | 4096 | 15.546 |
15.385 | 1.01x | 11.543 | 1.35x |
| Z1k256 | Z1 with top-k 256 | 16384 | 270336 | 2 | 256 | 11.476 |
11.499 | 1.00x | 11.482 | 1.00x |
| Z2 | 8 x 32k documents, full causal | 262144 | 262144 | 8 | 2048 |
31.797 | 31.452 | 1.01x | 33.880 | 0.94x |
| Z2cp | 8 x 32k documents, CP16 zigzag rank 0 | 16384 | 270336 | 16 |
2048 | 2.024 | 2.005 | 1.01x | 2.471 | 0.82x |
| Z3 | packed 4k-64k documents, full causal | 169984 | 169984 | 8 | 2048
| 24.578 | 24.352 | 1.01x | 26.741 | 0.92x |
| Z3cp | packed 4k-64k documents, CP16 zigzag rank 0 | 10624 | 175296 |
16 | 2048 | 1.791 | 1.764 | 1.02x | 1.910 | 0.94x |
| P1sink | recorded P1 geometry with sink statistics | 16231 | 268757 |
8 | 2048 | 3.739 | 3.696 | 1.01x | 3.673 | 1.02x |
| S4sink | one 64k causal document, sink statistics | 65536 | 65536 | 1
| 2048 | 14.987 | 14.861 | 1.01x | 14.126 | 1.06x |
| S6sink | one 262k causal document, sink statistics | 262144 | 262144 |
1 | 2048 | 196.862 | 196.299 | 1.00x | 186.265 | 1.06x |
| P1 | recorded packed call | 16231 | 268757 | 8 | 2048 | 3.426 | 3.404
| 1.01x | 3.404 | 1.01x |
| P1_peaked | P1 with dominating keys | 16231 | 268757 | 8 | 2048 |
3.438 | 3.406 | 1.01x | 3.435 | 1.00x |
| P2 | second recorded token count, boundaries derived | 16172 | 267520
| 8 | 2048 | 3.431 | 3.403 | 1.01x | 3.435 | 1.00x |
| P3 | P1 with top-k 4096 | 16231 | 268757 | 8 | 4096 | 3.700 | 3.677 |
1.01x | 3.683 | 1.00x |
| S1 | single causal document N = 8192 | 8192 | 8192 | 1 | 2048 | 0.413
| 0.413 | 1.00x | 0.414 | 1.00x |
| S2 | single causal document N = 16384 | 16384 | 16384 | 1 | 2048 |
1.210 | 1.197 | 1.01x | 1.208 | 1.00x |
| S3 | single causal document N = 32768 | 32768 | 32768 | 1 | 2048 |
3.805 | 3.757 | 1.01x | 3.800 | 1.00x |
| S4 | single causal document N = 65536 | 65536 | 65536 | 1 | 2048 |
13.682 | 13.556 | 1.01x | 13.621 | 1.00x |
| S5 | single causal document N = 131072 | 131072 | 131072 | 1 | 2048 |
49.979 | 49.468 | 1.01x | 49.560 | 1.01x |
| S6 | single causal document N = 262144 | 262144 | 262144 | 1 | 2048 |
189.808 | 188.905 | 1.00x | 189.138 | 1.00x |
| S7 | single causal document N = 524288 | 524288 | 524288 | 1 | 2048 |
780.558 | 780.703 | 1.00x | 780.628 | 1.00x |
| S4_peaked | S4 with dominating keys | 65536 | 65536 | 1 | 2048 |
13.569 | 13.442 | 1.01x | 13.525 | 1.00x |
| C1 | CP tail 4096 x 65536 | 4096 | 65536 | 1 | 2048 | 1.569 | 1.557 |
1.01x | 1.566 | 1.00x |
| C2 | CP tail 4096 x 131072 | 4096 | 131072 | 1 | 2048 | 2.967 | 2.944
| 1.01x | 2.948 | 1.01x |
| C3 | packed 8 x (2048 x 32768) | 16384 | 262144 | 8 | 2048 | 3.237 |
3.219 | 1.01x | 3.214 | 1.01x |
| V1 | N = 65536, ratio 2 | 65536 | 32768 | 1 | 2048 | 7.602 | 7.517 |
1.01x | 7.567 | 1.00x |
| V2 | N = 65536, top-k 256 | 65536 | 65536 | 1 | 256 | 12.453 | 12.457
| 1.00x | 12.456 | 1.00x |
| V3 | N = 65536, top-k 4096 | 65536 | 65536 | 1 | 4096 | 14.693 |
14.566 | 1.01x | 14.617 | 1.01x |
| S8 | single causal document N = 1048576 | 1048576 | 1048576 | 1 | 2048
| 3358.356 | 3357.750 | 1.00x | 3358.438 | 1.00x |

Cake ships no other variant of this kernel; its non-wide
ascending-tile-order scan programs (the sm_103a narrow, l6, split,
split-l6 and paired-CTA programs and the sm_100a l6 program) gain the
`far_sample` statistic, the wide and descending programs only take the
new scalar, per-program compile flags change the generated code of
several sm_100a and sm_103a programs, and the family ships on sm_100a
(GB200), sm_103a (GB300) and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a `far_sample` setting to control tile sampling for
ascending-order scans. It can be set to `0` or `1`; when unspecified,
the architecture’s default is used. Descending-order and wide scans are
unaffected.
* Added benchmark options and usage guidance for evaluating far
sampling, including A/A comparisons.
* **Documentation**
  * Clarified the sampling behavior and its effect on results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [431c968](https://github.com/flashinfer-ai/flashinfer/commit/431c9687f3bb9a048e194c74a178d7cfb02b1585)

- **作者**: eigen
- **时间**: 2026-10-24T08:14:06Z
- **提交信息**: perf(cake_kda): with grad; hints-off fused gradient from 16 heads and the 64-column token-row saving forward on SM107 (#7158)

The packed KDA chunked training forward and backward has one Cake
variant: BF16 tensors with an FP32 gate, laid out as `[1, S, H, 128]`;
its saving forward stores a saved set for the backward in `light`
(default) or `tape` mode; a no-save forward pairs with a
checkpoint-replay backward. This PR changes the dispatch of that variant
on SM107 (`sm_107a`) only: from 16 heads the fused gradient runs the
same kernel built with its L2 prefetch and evict-first hints off, and
where the saving forward's serial recurrence runs in its 64-column form
it now reads the saved token rows instead of internal copies; no kernel
source changes, and on SM100 (`sm_100a`) and SM103 (`sm_103a`) the
dispatch and the programs are unchanged. Against the previous Cake
version of this kernel on main, delivered by PR #7023 ("previous" in the
tables), the speedup on R200 (`sm_107a`, 208 SMs, CUDA 13.4) ranges from
0.9981× to 1.0394× over all 14 shapes and columns (forward
0.9985–1.0253×, backward 0.9981–1.0394×, checkpoint forward + backward
0.9993–1.0219×), with outputs bitwise identical to the previous version
on every shape. On B200 (`sm_100a`, 148 SMs) and GB300 (`sm_103a`, 152
SMs), CUDA 13.4, the same 14 shapes compare the package on main with
this PR's re-rendered package (the same programs): 0.9897–1.0141× on
B200 and 0.9948–1.0051× on GB300, outputs bitwise identical, no
regression. In those two tables the third column (`ckpt-replay bwd`)
measures the checkpoint-replay backward alone; in the R200 table it
measures the checkpoint forward + backward.

**NVIDIA R200 (sm_107a, 208 SMs), CUDA 13.4** -- all 14 shapes; previous
= the Cake version on main, this PR = the new dispatch. The dispatch
change touches only the rows of 16 heads or more (P12, P13, P14: the
fused gradient's hints-off builds; P14's saving forward also takes the
64-column token-row recurrence); the other rows run the previous
programs, and their ratios near 1.00× show no regression

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt fwd+bwd previous / this PR ms | ckpt
fwd+bwd speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 0.8861 / 0.8870 | 0.9989× | 2.1782 / 2.1774 |
1.0003× | 3.9499 / 3.9480 | 1.0005× |
| P2 (H=4, S=245028) | 0.8902 / 0.8894 | 1.0009× | 2.2067 / 2.2110 |
0.9981× | 3.9834 / 3.9829 | 1.0001× |
| P3 (H=4, S=249866) | 0.8994 / 0.8964 | 1.0034× | 2.2576 / 2.2593 |
0.9993× | 4.0525 / 4.0467 | 1.0014× |
| P4 (H=4, S=250340) | 0.9057 / 0.9067 | 0.9988× | 2.2497 / 2.2492 |
1.0002× | 4.0622 / 4.0596 | 1.0007× |
| P5 (H=4, S=258574) | 0.9239 / 0.9238 | 1.0002× | 2.3305 / 2.3321 |
0.9993× | 4.1734 / 4.1700 | 1.0008× |
| P6 (H=4, S=259042) | 0.9282 / 0.9290 | 0.9992× | 2.3280 / 2.3267 |
1.0006× | 4.1812 / 4.1816 | 0.9999× |
| P7 (H=4, S=259584) | 0.9169 / 0.9164 | 1.0005× | 2.3228 / 2.3190 |
1.0016× | 4.1507 / 4.1498 | 1.0002× |
| P8 (H=4, S=261393) | 0.9361 / 0.9359 | 1.0003× | 2.3445 / 2.3403 |
1.0018× | 4.2095 / 4.2112 | 0.9996× |
| P9 (H=1, S=261393) | 0.3275 / 0.3274 | 1.0004× | 0.6828 / 0.6831 |
0.9996× | 1.3347 / 1.3356 | 0.9993× |
| P10 (H=2, S=261393) | 0.5176 / 0.5183 | 0.9985× | 1.2465 / 1.2481 |
0.9988× | 2.2811 / 2.2803 | 1.0003× |
| P11 (H=8, S=261393) | 1.7492 / 1.7508 | 0.9991× | 4.5489 / 4.5432 |
1.0013× | 8.0470 / 8.0474 | 0.9999× |
| P12 (H=16, S=261393) | 3.6493 / 3.6527 | 0.9991× | 10.3523 / 9.9604 |
1.0394× | 17.6424 / 17.3793 | 1.0151× |
| P13 (H=32, S=261393) | 5.2326 / 5.2377 | 0.9990× | 18.8771 / 18.4597 |
1.0226× | 29.3356 / 28.9509 | 1.0133× |
| P14 (H=64, S=261393) | 11.8178 / 11.5266 | 1.0253× | 36.9433 / 36.1789
| 1.0211× | 60.5478 / 59.2501 | 1.0219× |

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4** -- the dispatch on this
GPU is unchanged; previous = the package on main, this PR = the same
programs re-rendered (no regression; outputs bitwise)

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt-replay bwd previous / this PR ms |
ckpt-replay bwd speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 1.4708 / 1.4660 | 1.0033× | 3.3190 / 3.3068 |
1.0037× | 4.4009 / 4.3995 | 1.0003× |
| P2 (H=4, S=245028) | 1.4729 / 1.4692 | 1.0025× | 3.3883 / 3.3704 |
1.0053× | 4.5582 / 4.5365 | 1.0048× |
| P3 (H=4, S=249866) | 1.5160 / 1.4950 | 1.0141× | 3.4391 / 3.4474 |
0.9976× | 4.6750 / 4.6279 | 1.0102× |
| P4 (H=4, S=250340) | 1.5080 / 1.5031 | 1.0033× | 3.4376 / 3.4385 |
0.9997× | 4.7020 / 4.6550 | 1.0101× |
| P5 (H=4, S=258574) | 1.5435 / 1.5395 | 1.0026× | 3.5575 / 3.5606 |
0.9991× | 4.7940 / 4.8039 | 0.9979× |
| P6 (H=4, S=259042) | 1.5362 / 1.5324 | 1.0025× | 3.5585 / 3.5604 |
0.9995× | 4.7860 / 4.7725 | 1.0028× |
| P7 (H=4, S=259584) | 1.5325 / 1.5274 | 1.0034× | 3.5530 / 3.5538 |
0.9998× | 4.7912 / 4.8106 | 0.9960× |
| P8 (H=4, S=261393) | 1.5522 / 1.5462 | 1.0039× | 3.5915 / 3.5930 |
0.9996× | 4.8337 / 4.8619 | 0.9942× |
| P9 (H=1, S=261393) | 0.5457 / 0.5440 | 1.0031× | 1.0459 / 1.0460 |
0.9999× | 1.4207 / 1.4197 | 1.0007× |
| P10 (H=2, S=261393) | 0.8802 / 0.8782 | 1.0023× | 1.9173 / 1.9161 |
1.0006× | 2.5846 / 2.5811 | 1.0013× |
| P11 (H=8, S=261393) | 2.9179 / 2.8973 | 1.0071× | 7.2746 / 7.1736 |
1.0141× | 9.3499 / 9.3614 | 0.9988× |
| P12 (H=16, S=261393) | 5.5525 / 5.5418 | 1.0019× | 15.2416 / 15.2987 |
0.9963× | 17.8876 / 17.8959 | 0.9995× |
| P13 (H=32, S=261393) | 8.9282 / 9.0209 | 0.9897× | 28.8934 / 28.9808 |
0.9970× | 34.4469 / 34.5033 | 0.9984× |
| P14 (H=64, S=261393) | 18.2812 / 18.2718 | 1.0005× | 55.6990 / 55.7740
| 0.9987× | 66.7401 / 66.8432 | 0.9985× |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4** -- the dispatch on this
GPU is unchanged; previous = the package on main, this PR = the same
programs re-rendered (no regression; outputs bitwise)

| Shape (H, S) | fwd previous / this PR ms | fwd speedup | bwd previous
/ this PR ms | bwd speedup | ckpt-replay bwd previous / this PR ms |
ckpt-replay bwd speedup |
|---|---|---|---|---|---|---|
| P1 (H=4, S=239718) | 1.4121 / 1.4066 | 1.0039× | 3.0836 / 3.0876 |
0.9987× | 4.0936 / 4.0888 | 1.0012× |
| P2 (H=4, S=245028) | 1.4271 / 1.4256 | 1.0010× | 3.1727 / 3.1740 |
0.9996× | 4.1562 / 4.1641 | 0.9981× |
| P3 (H=4, S=249866) | 1.4416 / 1.4393 | 1.0016× | 3.2160 / 3.2219 |
0.9982× | 4.2314 / 4.2180 | 1.0032× |
| P4 (H=4, S=250340) | 1.4497 / 1.4506 | 0.9994× | 3.2293 / 3.2330 |
0.9989× | 4.2522 / 4.2522 | 1.0000× |
| P5 (H=4, S=258574) | 1.4854 / 1.4858 | 0.9997× | 3.3240 / 3.3278 |
0.9988× | 4.3677 / 4.3614 | 1.0014× |
| P6 (H=4, S=259042) | 1.4791 / 1.4802 | 0.9993× | 3.3163 / 3.3300 |
0.9959× | 4.3433 / 4.3488 | 0.9987× |
| P7 (H=4, S=259584) | 1.4752 / 1.4730 | 1.0015× | 3.3163 / 3.3195 |
0.9991× | 4.3433 / 4.3515 | 0.9981× |
| P8 (H=4, S=261393) | 1.4928 / 1.4925 | 1.0002× | 3.3604 / 3.3595 |
1.0003× | 4.3944 / 4.4044 | 0.9977× |
| P9 (H=1, S=261393) | 0.5609 / 0.5608 | 1.0001× | 1.0193 / 1.0219 |
0.9975× | 1.3773 / 1.3808 | 0.9974× |
| P10 (H=2, S=261393) | 0.8708 / 0.8663 | 1.0051× | 1.8186 / 1.8254 |
0.9963× | 2.4272 / 2.4398 | 0.9948× |
| P11 (H=8, S=261393) | 2.7252 / 2.7323 | 0.9974× | 6.4643 / 6.4685 |
0.9993× | 8.3718 / 8.3781 | 0.9992× |
| P12 (H=16, S=261393) | 5.2042 / 5.1972 | 1.0013× | 13.4316 / 13.4400 |
0.9994× | 15.8962 / 15.9162 | 0.9987× |
| P13 (H=32, S=261393) | 7.8989 / 7.8992 | 1.0000× | 24.7127 / 24.7107 |
1.0001× | 29.5644 / 29.6316 | 0.9977× |
| P14 (H=64, S=261393) | 16.0880 / 16.1004 | 0.9992× | 47.5057 / 47.5409
| 0.9993× | 57.4619 / 57.5261 | 0.9989× |

Cake ships no other data type, layout or form of this kernel; the family
covers `sm_100a`, `sm_103a` and `sm_107a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added additional Cake KDA training kernel options for supported
workloads, including optimized paths for `sm_107a`.
* **Improvements**
* Improved kernel selection for saved-forward workloads on `sm_107a`;
other supported architectures retain their existing paths.
* Added a no-prefetch-hint option for certain fused-gradient workloads
on `sm_107a` with 16 or more heads.
* **Bug Fixes**
* Training calls now reject sequence counts outside the supported range
of 1–256 with a clear error.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4706
- **最后更新**: 2026-10-24T23:29:49Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Kyle Hu, Aryan Kumar

## AI分析总结

## FastVideo 昨日提交分析（CI/基础设施类更新）

### 1. 主要更新类型
- **持续集成（CI）配置更新**为主，属于基础设施与工具链优化，包含少量配套文档更新。非功能新增或Bug修复。

### 2. 关键变更点与项目方向的关系
- 引入 **Spark4 CI 后端路由**（#2014），并同步补充文档，使 CI 能将构建任务分发到 Spark4 后端。
- 新增 **启用 FA2（FlashAttention 2）的 Spark CI 镜像**及 **GB10 平台参考配置**（#2017），扩大 CI 的硬件与算子覆盖。
- 这些变更与 FastVideo 作为"高性能视频生成推理/训练框架"的定位一致：FA2 是视频扩散模型加速的核心算子，CI 中提前验证其在 Spark/GB10 环境下的可用性，直接服务于性能优化目标。

### 3. 对项目的影响与潜在意义
- **提升回归测试覆盖面**：新镜像与路由让 PR 能在更多异构硬件上自动验证，降低性能回归风险。
- **加速开发流程**：CI 后端路由可能改善构建吞吐与等待时间，配合项目已有的周度开发会议（Weekly Dev Meeting），强化了迭代效率。
- **为多硬件生态铺路**：GB10 参考配置暗示项目正在扩展对新兴推理平台的支持，有利于生态外延。

### 4. 值得关注的技术点
- **FA2 进入 CI**：意味着以后对 Attention 实现的改动都可能被自动测试，属于对性能敏感路径的守护。
- **CI 后端路由机制**：值得关注其调度策略（如按硬件标签分流），可能影响贡献者的 PR 触发规则。
- Spark4/GB10 属于较新的目标平台，需留意后续是否会有对应的运行时适配代码合入。

### 5. 结合项目背景的影响评估
README 显示 FastVideo 强调快速上手、文档完备与社区协作（Slack、Cookbook、文档站）。本次提交虽不直接改功能，但通过**夯实 CI 基础设施**，为后续在多硬件上的性能优化与功能迭代提供了可靠的验证保障——这正是一个以"Fast"为核心卖点的项目可持续发展的隐性支柱，属于支撑长期演进的必要投入。

## 详细提交记录

### [a92c5c1](https://github.com/hao-ai-lab/FastVideo/commit/a92c5c1578b322b9d6691723c6b6a669b9fe7370)

- **作者**: Kyle Hu
- **时间**: 2026-10-24T23:29:44Z
- **提交信息**: [docs]: add spark4 CI backend routing (#2014)

Co-authored-by: Aryan Kumar <aryank@Aryans-Mac-Studio.local>

### [dfc5550](https://github.com/hao-ai-lab/FastVideo/commit/dfc5550c35006635a6ec9e8b2b5ba5c85ed458ec)

- **作者**: Aryan Kumar
- **时间**: 2026-10-24T23:16:25Z
- **提交信息**: [ci] Add FA2-enabled Spark CI image and GB10 reference setup (#2017)

Co-authored-by: Aryan Kumar <aryank@Aryans-Mac-Studio.local>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34794
- **最后更新**: 2026-10-24T23:18:23Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-10-19T05:38:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13300
- **最后更新**: 2026-10-24T19:16:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37799
- **最后更新**: 2026-10-25T00:19:48Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 8
- **主要提交者**: Xiaoyu Zhang, Mick, Vladimir (Vova) Vagaytsev

## AI分析总结

## sgl-project/sglang 昨日提交分析

### 1. 主要更新类型

- **性能优化（约 15 条，占 60%）**：绝大多数提交以 `[Perf]` 标记，集中在 diffusion（扩散模型）推理链路。
- **Bug 修复（约 8 条）**：涉及 AMD GPU allreduce、diffusion 调度、request logger、minimax-m3 模型等。
- **重构（1 条）**：插件内核后端的架构拆分。

### 2. 关键变更点及与项目方向的关系

- **Diffusion 模型推理深度优化（核心主题）**：超过半数提交针对 diffusion 模型，涵盖 Wan（视频生成）、LTX-2.5、Cosmos3、LTX VAE 等多个具体模型。优化方向包括：消除不必要的主机同步、融合 RMSNorm 与 RoPE、并行化 VAE 解码、流水线通信去冗余、CUDA Graph 支持等。这表明 SGLang 正将 LLM 高性能推理经验系统性迁移到多模态扩散模型领域。
- **大模型模型适配**：GLM-5.3 分段式 chat template 编码（TTFT 提升约 10%）、DSv4 分页 KV cache 量化向量化、GPT-OSS SwiGLU 融合 Triton 内核、minimax-m3 工具调用修复，体现对前沿开源模型的持续跟进。
- **KV Cache 分布式优化**：0SM（零 SM 占用）KV Cache Allgather 实现了一种极低开销的 KV 分片通信方案，对大规模分布式推理有重要意义。
- **插件化内核架构**：将插件内核后端从 srt 集成中拆分，为第三方内核扩展提供清晰契约，属于基础设施级重构。
- **硬件适配扩展**：B300（Blackwell）上优先使用 FA4 替代 cuDNN SDPA；cu134 镜像选版调整；AMD custom-allreduce 修复，体现对多硬件生态（NVIDIA 新旧架构 + AMD）的全面支持。

### 3. 对项目的影响和潜在意义

- **Diffusion 推理成熟度大幅提升**：大量去除主机同步、优化内存拷贝和数据连续性的提交，使扩散模型推理从"能跑"走向"高效跑"，降低延迟与 GPU 利用率浪费。
- **实时推理能力增强**：diffusion/realtime 帧载荷连续性修复、idle loop 修复等问题修复，为实时视频/图像生成场景的可靠性提供保障。
- **多硬件竞争力巩固**：AMD 修复 + Blackwell/B300 针对性优化，使 SGLang 在多样化硬件部署中保持领先。

### 4. 值得关注的技术点

- **0SM KV Allgather**：几乎不占用 SM 的 KV 通信方案，是分布式推理通信的创新。
- **插件内核后端拆分**：为生态扩展（如自定义算子、第三方硬件内核）打开接口，是长期架构投资。
- **GLM-5.3 分段编码 + 分词器缓存**：利用 chat template 的特殊 token 作为切分点实现无损增量编码，方法优雅且通用。
- **diffusion 中大量 "off host" 优化模式**：反复出现的"消除主机同步""避免临时 GPU 张量""流水线通信去冗余"，形成了一套可复用的 GPU 推理优化范式。

### 5. 对项目整体发展的影响

结合 README 中"SGLang 专注 LLM 与多模态模型快速推理"的定位，这批提交清晰展示了两大战略方向：**一是将 diffusion 多模态推理打造成与 LLM 推理同等成熟的第二条产品线**，通过持续的性能打磨和稳定性修复缩小与专用推理框架的差距；**二是持续巩固 LLM 推理的核心竞争力**，通过前沿模型（GLM-5.3、DSv4、GPT-OSS、minimax-m3）的快速适配和分布式基础设施创新（0SM KV sharding、插件化内核）保持技术领先。整体而言，项目正从单一 LLM 推理引擎演进为统一的 LLM + 多模态高性能推理平台。

## 详细提交记录

### [6563312](https://github.com/sgl-project/sglang/commit/656331295619a4d0267b40b7da0b5cd5b549fcbc)

- **作者**: Vladimir (Vova) Vagaytsev
- **时间**: 2026-10-24T22:36:01Z
- **提交信息**: [Fix] [AMD] custom-allreduce: Stop registering oversized inputs in the deterministic all-reduce (#34543)

### [773cb93](https://github.com/sgl-project/sglang/commit/773cb938fe9484a8f7e7e46fb1b1fe96412c59ed)

- **作者**: Mick
- **时间**: 2026-10-24T16:27:26Z
- **提交信息**: [Fix] diffusion: Complete Blackwell routing test fixture (#46294)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [059ba6b](https://github.com/sgl-project/sglang/commit/059ba6b66669b9acf4eca833e6f72abeccec9be4)

- **作者**: Ke Bao
- **时间**: 2026-10-24T15:38:47Z
- **提交信息**: [Chore] docker: Select released wheels and the torch index in the cu134 image (#46136)

Co-authored-by: zhongyu <zhongyu@minimaxi.com>

### [bf1a252](https://github.com/sgl-project/sglang/commit/bf1a2529538fa5225ad46552795cfa6b3863fa0c)

- **作者**: Ke Bao
- **时间**: 2026-10-24T14:27:08Z
- **提交信息**: [Perf] moe: Run the Marlin GPT-OSS SwiGLU through the fused Triton kernel (#46134)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>

### [d0f5171](https://github.com/sgl-project/sglang/commit/d0f517168dffabc38e29040713ddfedccab7fa6a)

- **作者**: Ke Bao
- **时间**: 2026-10-24T14:11:12Z
- **提交信息**: [Fix] minimax-m3: Type nested tool-call arguments and count self-opened reasoning (#46133)

Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Yan Huang <yan.huang@radixark.ai>

### [13b7ef7](https://github.com/sgl-project/sglang/commit/13b7ef75c577005b3393316af3c5f1f5e0778a4a)

- **作者**: Mick
- **时间**: 2026-10-24T13:36:26Z
- **提交信息**: [Perf] diffusion: Keep same-device copies out of the pipelined Ulysses exchange (#46145)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [625399c](https://github.com/sgl-project/sglang/commit/625399c7d2ffa096920d1924ef9604668acbf1bb)

- **作者**: Mick
- **时间**: 2026-10-24T13:35:18Z
- **提交信息**: [Fix] diffusion/realtime: Keep frame payloads contiguous (#46250)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [c9f4055](https://github.com/sgl-project/sglang/commit/c9f40557e67755690513546b5582b1ba316b78ba)

- **作者**: Mick
- **时间**: 2026-10-24T13:33:27Z
- **提交信息**: [Perf] diffusion: Remove per-step host syncs and uploads in image models (#46046)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [93d70b3](https://github.com/sgl-project/sglang/commit/93d70b3802090bdf8996d8b40ed2ff8eb5aee3e6)

- **作者**: Mick
- **时间**: 2026-10-24T13:32:02Z
- **提交信息**: [Perf] diffusion: Gather spatial-parallel decode heights on the host (#46171)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6df9015](https://github.com/sgl-project/sglang/commit/6df9015b4fb0da6cb51f0528a782009f946bc3c2)

- **作者**: Mick
- **时间**: 2026-10-24T13:30:57Z
- **提交信息**: [Perf] diffusion: Fuse Wan's q/k RMSNorm with its interleaved RoPE (#46228)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8bf8866](https://github.com/sgl-project/sglang/commit/8bf88667fd4a13f188c3a388c6109ac178d13e30)

- **作者**: Mick
- **时间**: 2026-10-24T13:29:49Z
- **提交信息**: [Perf] diffusion: Stop the idle loop from starving async-save replies (#46221)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a9b23e9](https://github.com/sgl-project/sglang/commit/a9b23e98c755b50c36d55269c7eca8546457e38c)

- **作者**: Mick
- **时间**: 2026-10-24T13:28:18Z
- **提交信息**: [Fix] diffusion/loader: Honor custom weight-loader overrides (#46253)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [fe1bd10](https://github.com/sgl-project/sglang/commit/fe1bd108372c9ba2ab959fcf99cf196433d155d5)

- **作者**: Shijin Zhang
- **时间**: 2026-10-24T13:11:14Z
- **提交信息**: [Perf] glm-5.3: Encode GLM-5.3 Python chat template prompts segment by segment

GLM-5.3 and GLM-5.3-Flash prompts are encoded segment by segment: the Python chat template hands its special tokens to the encoder as cut points, the text between them goes through one encode_batch call at any prompt length, and the ids of recurring parts (system prompt, tool list, earlier turns) are cached per tokenizer. Prompts and token ids are unchanged; GLM-5.3-Flash TTFT improves by ~10%.

### [052feb7](https://github.com/sgl-project/sglang/commit/052feb72a8c9df07e6a44a898816712bcb93ae9d)

- **作者**: Yuan Luo
- **时间**: 2026-10-24T12:36:40Z
- **提交信息**: [Perf] dsv4: Vectorize paged KV cache dequantization (#42929)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [b86d294](https://github.com/sgl-project/sglang/commit/b86d294a980bb7fab27a82594a343838635b5e84)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-24T12:12:00Z
- **提交信息**: [Refactor] kernels: Add the plugin kernel backend and split plugin contracts from their srt integration (#45389)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3ea7e21](https://github.com/sgl-project/sglang/commit/3ea7e210d28e26a13590d3244cedfe17f8c3e58c)

- **作者**: Shunkangz
- **时间**: 2026-10-24T09:40:18Z
- **提交信息**: [Perf] KVShard: 0SM KV Cache Allgather for KV Cache Sharding (#44029)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [406786f](https://github.com/sgl-project/sglang/commit/406786fd910dd82d03d1ce2c2e4c08b547786bc2)

- **作者**: metamergebot
- **时间**: 2026-10-24T08:50:13Z
- **提交信息**: [Fix] request_logger: Skip watermark redaction when watermarking is disabled (#46207)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [638374c](https://github.com/sgl-project/sglang/commit/638374c3893f7a0e00ba8aa4ca3b58b16eeb8f4b)

- **作者**: Mick
- **时间**: 2026-10-24T07:45:09Z
- **提交信息**: [Fix] diffusion/scheduler: Isolate invalid IPC requests (#46157)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [5ac018b](https://github.com/sgl-project/sglang/commit/5ac018b2516352c82a7cf446b534766624610b22)

- **作者**: Mick
- **时间**: 2026-10-24T07:43:42Z
- **提交信息**: [Perf] diffusion: Encode Cosmos3 video while it decodes (#46172)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick <mickqian@radixark.ai>

### [af7d941](https://github.com/sgl-project/sglang/commit/af7d941fc3b6358c28ed52f4dd55120dca7191f6)

- **作者**: Mick
- **时间**: 2026-10-24T07:42:57Z
- **提交信息**: [Perf] diffusion: Validate breakable CUDA graphs for LTX-2.5 two-stage serving (#46239)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [31b352b](https://github.com/sgl-project/sglang/commit/31b352b8ea1bf7643eb2af03ef4a23f6085d85b8)

- **作者**: Mick
- **时间**: 2026-10-24T07:42:20Z
- **提交信息**: [Fix] diffusion: Preserve metrics collectives after output save errors (#46235)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [19212d1](https://github.com/sgl-project/sglang/commit/19212d19b5dfe151040972315faae193095fb632)

- **作者**: Mick
- **时间**: 2026-10-24T07:40:29Z
- **提交信息**: [Perf] diffusion: Keep shared denoising paths off the host and add host-sync test guards (#46045)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0b73cc0](https://github.com/sgl-project/sglang/commit/0b73cc01c049f04e676b2a65181875c23a828a34)

- **作者**: Mick
- **时间**: 2026-10-24T07:39:05Z
- **提交信息**: [Perf] diffusion: Prefer FA4 over cuDNN SDPA for long self-attention on B300 (#46146)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d301348](https://github.com/sgl-project/sglang/commit/d30134818c0b96e5e6981dc6845dadabf20df2ba)

- **作者**: Mick
- **时间**: 2026-10-24T07:38:27Z
- **提交信息**: [Perf] diffusion: Split LTX tiled VAE decode across the decode-parallel ranks (#46237)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1d0f90b](https://github.com/sgl-project/sglang/commit/1d0f90bf2bba674c243efa2793d1637b01606da4)

- **作者**: Mick
- **时间**: 2026-10-24T07:36:46Z
- **提交信息**: [Perf] diffusion/loader: Avoid temporary GPU tensors when loading encoders (#46241)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1293
- **最后更新**: 2026-10-23T10:31:32Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 95343
- **最后更新**: 2026-10-25T00:05:54Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 17
- **主要提交者**: Jared Wen, Roy Wang, xaguilar-amd

## AI分析总结

## vLLM 昨日提交分析（17条）

### 1. 主要更新类型
- **性能优化**（约6条）：占比最大，包括MLA内核优化、ROCm/AMD平台加速、量化GEMV内核等
- **功能新增**（约4条）：自适应验证采样、HTTP profiling扩展、共享查找/传输/可观测性（UMBP）
- **Bug修复与兼容性**（约4条）：ModelOpt混合精度草稿加载、MoRIIO资源释放、CI引用修复等
- **弃用清理**（1条）：弃用LM Format Enforcer结构化输出后端
- **CI/工具链**（约3条）：标签自动化、测试稳定性、请求头处理修复

### 2. 关键变更点及与项目方向的关系
项目目标是"为所有人提供简单、快速、廉价的LLM服务"，本批提交与之高度契合：
- **AMD/ROCm生态持续深化**：约6条提交涉及ROCm，包括MI325X/MI355X上DeepSeek-V4支持、RDNA3的W4A8 int8 GEMV内核、MiniMax-M3 Indexer等，直接扩大"廉价"服务的硬件覆盖范围，降低对NVIDIA的依赖。
- **内核级性能压榨**：FlashInfer升级到0.7.2.post1、`concat_and_cache_mla`跳过scale计算（1.2%~3.0% TPOT提升），持续兑现"快速"承诺。
- **投机解码（Spec Decode）完善**：ModelOpt混合精度DFlash/DSpark草稿加载修复、Kimi-K3 DSpark测试调整，表明投机解码正走向生产成熟。
- **采样能力扩展**：批分片采样支持自适应验证，提升分布式采样的吞吐与灵活性。

### 3. 对项目的影响和潜在意义
- **弃用LM Format Enforcer**标志着结构化输出后端收敛，可能以XGrammar等为主力，降低维护负担。
- **Profiling支持profile_prefix**使开发者能按模型前缀精准性能分析，对大规模生产部署的调优价值显著。
- **UMBP系列（3/10）**说明这是一套多阶段的统一内存/传输/观测基础设施，后续会持续增强分布式效率。
- 大量AMD贡献者与AI agent（Codex、Claude、Cursor等）协同署名，反映vLLM社区的硬件多元化与AI辅助开发模式已成常态。

### 4. 值得关注的技术点
- **Monokernel**在MI325X上的启用（DeepSeek ROCm V4.1-Flash），单内核融合是性能优化新路径。
- **W4A8 int8-dot混合MXFP4 GEMV**：将量化权重与MXFP4激活结合，面向消费级RDNA GPU的低成本部署有重要意义。
- **DCP MLA验证环境变量删除**：说明ROCm MLA路径已足够稳定，从实验特性转正。
- **AI协同开发**：多条提交以vllm-agent、Codex等为共同作者，体现了vLLM在AI辅助工程上的前沿实践。

### 5. 对项目发展的整体影响
结合README的"人人可用的LLM服务"愿景，这批提交呈现三重推进：其一，**硬件民主化**——AMD全系（数据中心MI系列到桌面RDNA）的持续投入，真正降低LLM服务门槛；其二，**性能纵深**——从内核、采样到投机解码全链路优化，巩固vLLM作为最快推理引擎之一的地位；其三，**工程成熟度**——弃用陈旧后端、完善profiling与CI自动化，为生产级用户（Kimi-K3、DeepSeek等大客户）提供更可靠的基础。项目正从"能跑"向"跑得省、跑得稳"加速演进，同时社区治理已形成厂商（AMD/NVIDIA）与AI agent深度协作的成熟模式。

## 详细提交记录

### [4e59165](https://github.com/vllm-project/vllm/commit/4e591657157a021cab997f911d67f50c0d18a71e)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-24T22:19:14Z
- **提交信息**: [Deprecation] Deprecate LM Format Enforcer structured outputs backend (#63423)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7050ef8](https://github.com/vllm-project/vllm/commit/7050ef881ff0835f6890a47db1859a24c65481d6)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-24T20:35:17Z
- **提交信息**: [Sampling] Add adaptive verification support to batch-sharded sampling (#58466)

### [56e4e42](https://github.com/vllm-project/vllm/commit/56e4e42868b4652c66cb009928ddcee859b0d3c9)

- **作者**: Wentao Ye
- **时间**: 2026-10-24T20:26:19Z
- **提交信息**: [GLM 5.3 Perf] Skip scale calculation for `concat_and_cache_mla`, 1.2% ~ 3.0% E2E TPOT improvement (#62102)

### [dd5e754](https://github.com/vllm-project/vllm/commit/dd5e754494b48900748044dbd5eaba49d5637841)

- **作者**: Rushabh Lalwani
- **时间**: 2026-10-24T20:22:11Z
- **提交信息**: [Profiling] Add support for profile_prefix payload in HTTP /start_profile endpoint (#51974)

Signed-off-by: Rushabh Lalwani <rlalwani@google.com>
Co-authored-by: Rushabh Lalwani <rlalwani@google.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e7473bf](https://github.com/vllm-project/vllm/commit/e7473bf6862289f0647d1f4b01498288b181e063)

- **作者**: Jee Jee Li
- **时间**: 2026-10-24T16:22:16Z
- **提交信息**: [Kernel] Bump up FlashInfer to 0.7.2.post1 (#63466)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [be2de71](https://github.com/vllm-project/vllm/commit/be2de711989bb273e108c41f95d868122b154f9d)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-24T15:36:02Z
- **提交信息**: [CI][Bench] Keep captured request headers case-insensitive in Responses test (#63462)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5f63ea4](https://github.com/vllm-project/vllm/commit/5f63ea461ccd567ece6f50dd3701430c0f321039)

- **作者**: Sandeep Agrawal
- **时间**: 2026-10-24T12:28:36Z
- **提交信息**: [Bugfix][Quantization][Spec Decode] Load ModelOpt mixed-precision DFlash and DSpark drafts (#63001)

Signed-off-by: Sandeep Agrawal <sandeepa@nvidia.com>
Co-authored-by: Kotaro Yamamoto <kyamamoto@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c0f9fff](https://github.com/vllm-project/vllm/commit/c0f9fff649e732253c5472d3a4d28389605b4a01)

- **作者**: CharlesWu
- **时间**: 2026-10-24T12:25:43Z
- **提交信息**: [UMBP][3/10] Add shared lookup, transfer, hybrid, and observability (#61791)

Signed-off-by: CharlesWu <Charles.Wu@amd.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [7822663](https://github.com/vllm-project/vllm/commit/7822663cb48093a949835afc7af52ee13b0946ce)

- **作者**: frida-andersson
- **时间**: 2026-10-24T12:12:00Z
- **提交信息**: [DeepSeek][ROCm] V4.1-Flash: enable --monokernel on MI325X (#62713)

Signed-off-by: Frida Andersson <fanderss@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c0ba7e0](https://github.com/vllm-project/vllm/commit/c0ba7e01ffdd446a087df759e8c8c2bda28de2ea)

- **作者**: xiao-vllm_amd
- **时间**: 2026-10-24T12:09:43Z
- **提交信息**: [Perf][ROCm][Kernel] Add W4A8 int8-dot MXFP4 GEMV for RDNA3/RDNA3.5 d… (#60413)

Signed-off-by: Xiao Yu <xiao.yu.dc@outlook.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3950408](https://github.com/vllm-project/vllm/commit/39504080e56e6438207baba9100b0abf92758f85)

- **作者**: xaguilar-amd
- **时间**: 2026-10-24T12:08:44Z
- **提交信息**: [ROCm][MLA][DCP] Drop VLLM_ROCM_AITER_MLA_DCP_VERIFY (#61628)

Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cba669d](https://github.com/vllm-project/vllm/commit/cba669d45d127f56ed3e634074b620d2d16d05cd)

- **作者**: ukannika
- **时间**: 2026-10-24T12:03:34Z
- **提交信息**: [ROCm][PERF] Enable MiniMax-M3 Indexer CP (#57909)

Signed-off-by: ukannika <uma.kannikanti@amd.com>
Signed-off-by: ukannika_amdeng <uma.kannikanti@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [139feb4](https://github.com/vllm-project/vllm/commit/139feb45348d3eb303107a896e21303db3a0344e)

- **作者**: Fangzhou Ai
- **时间**: 2026-10-24T12:00:39Z
- **提交信息**: [ROCm][Perf][DSv4] Standalone mono decode layer for DeepSeek-V4-Pro on MI355X (#61482)

Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2aa7269](https://github.com/vllm-project/vllm/commit/2aa7269a837556bad5a16f1d6aa32916f7d14446)

- **作者**: TJian
- **时间**: 2026-10-24T11:53:20Z
- **提交信息**: [Bugfix][ROCm][MoRIIO] Release every prefill rank a READ holds (#62473)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Signed-off-by: TJian <tunjian.tan@embeddedllm.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [717cf84](https://github.com/vllm-project/vllm/commit/717cf843426ce85dbb7170aff7d7a833ad7d3c09)

- **作者**: Roy Wang
- **时间**: 2026-10-24T11:12:56Z
- **提交信息**: [CI] Label recipe PRs and link their recipes.vllm.ai preview (#63248)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Signed-off-by: Roy Wang <jasonailu87@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1bd56ea](https://github.com/vllm-project/vllm/commit/1bd56eaef38d0db35852fc38932d0c63003ef9f1)

- **作者**: Jared Wen
- **时间**: 2026-10-24T10:52:33Z
- **提交信息**: [CI][Kimi-K3] Expect no trailing-block drop in DSpark resend tests (#63449)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7a64fb8](https://github.com/vllm-project/vllm/commit/7a64fb8fc9239cb65e0df9313fa759594dfb206a)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-24T07:54:50Z
- **提交信息**: [CI] Fix the Domyn Edge (ROCm) and Qwen2 embed HF references (#63452)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-25
**监控日期**: 2026-10-24
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7337
- **最后更新**: 2026-10-24T23:42:07Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 12
- **主要提交者**: Yash Jain, ZhIMQ, haic0

## AI分析总结

## 一、主要更新类型

昨日提交以 **Bug修复** 为主（约6项），其次是 **CI/构建**（3项）、**功能新增/前端扩展**（2项）和 **性能/内核优化**（2项）。整体属于项目高频迭代期的稳定性与硬件适配加固阶段，而非大功能引入。

## 二、关键变更点与项目方向的关系

- **多模态（Omni）核心能力补强**：OmniVoice 长文本 TTS 生成支持（#6409）和 Qwen-Image 分块 VAE 解码缝隙修复（#8868）、扩散 LoRA 权重设备驻留修复（#8874），直接服务于 README 中"Easy, fast, cheap omni-modality serving"的定位，确保语音、图像、扩散等多模态链路在长输入和边缘场景下可用。
- **MI300/ROCm 硬件生态持续投入**：多条提交（#9307、#9320、#9276、#6662）围绕 AMD ROCm 平台展开——为 MI300 nightly 增加 Qwen3-Omni Seed-TTS 实时性能基准、筛选合格测试用例、修复 Hunyuan GroupNorm 回归检测、拆分 GroupNorm+SiLU 融合内核的 CTA 归约。这表明项目在积极拓宽 NVIDIA 之外的硬件后端，降低部署门槛。
- **MiniMax-H3 生态扩展**：ComfyUI 工作流 schema 修复、时间线指南、音乐视频工作流、TaylorSeer 警告等多条提交集中在 MiniMax-H3 模型的前端集成上，说明该项目正通过 ComfyUI 扩展吸引创作者社区。
- **CI 稳定性**：运行时 waiter 完成等待的稳定化（#9339）减少流水线抖动。

## 三、对项目的影响和潜在意义

这些提交共同提升项目的**生产就绪度**：长文本 TTS 和分块解码修复扩展了真实场景覆盖；ROCm 侧测试与基准的完善增强了跨平台回归防护；ComfyUI 工作流的持续产出扩大了下游用户群。短期内降低缺陷率，中期内强化 AMD 硬件和创意工具链两条增长线。

## 四、值得关注的技术点

- **融合 GroupNorm+SiLU 内核的多 CTA 归约拆分**（#6662）：涉及 GPU 归约通信设计，对扩散模型高分辨率推理有直接性能意义。
- **重计算抢占在无法回放解码状态的 AR 阶段直接失败**（#9249）：强化长上下文推理的正确性保障，避免静默状态错乱。
- **分块 VAE 解码尾块吸附消除拼接缝隙**（#8868）：图像质量的细节级修复。
- **AR-AI 辅助协作**：多个提交出现 Claude、Cursor 等 AI 共同署名，反映开发流程已深度人机协同。

## 五、结合 README 背景对项目发展的影响

README 强调"人人可用的 omni-modality 模型服务"。本批提交从三个维度推进该愿景：**可用性**（长文本 TTS、图像解码修复）、**可扩展性**（ROCm 基准与内核优化，覆盖更多硬件）、**易用性**（ComfyUI 工作流让非开发者也能编排多模态管线）。这些稳定性与生态类投入虽不耀眼，却正是服务框架从"能跑"走向"可信赖"的必经阶段，有助于吸引企业级和创作者用户，奠定项目在多模态服务赛道的差异化基础。

## 详细提交记录

### [285bd32](https://github.com/vllm-project/vllm-omni/commit/285bd327f84d3c72c2a0bdc7977ee957a27f7882)

- **作者**: lm10-arg
- **时间**: 2026-10-24T23:41:55Z
- **提交信息**: [CI/Build] Stabilize host runtime waiter completion wait (#9339)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [7f90d24](https://github.com/vllm-project/vllm-omni/commit/7f90d24d76705c8ee901a5d049a285fcbcbaa816)

- **作者**: akshatvishu
- **时间**: 2026-10-24T20:10:25Z
- **提交信息**: [BugFix][TTS] Support long-form OmniVoice generation (#6409)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [6a79869](https://github.com/vllm-project/vllm-omni/commit/6a798699d4af4bf56b755e7c7ed8ae3304742659)

- **作者**: lm10-arg
- **时间**: 2026-10-24T18:57:08Z
- **提交信息**: [Bugfix] Fix MiniMax-H3 ComfyUI workflow schemas (#9337)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [0dde197](https://github.com/vllm-project/vllm-omni/commit/0dde197a078f6ab5be474bc6e201619e37119de7)

- **作者**: haic0
- **时间**: 2026-10-24T17:40:07Z
- **提交信息**: [CI/Build][ROCm] Add Qwen3-Omni Seed-TTS realtime perf to MI300 nightly (#9307)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [de43bb0](https://github.com/vllm-project/vllm-omni/commit/de43bb05b5e5bc6c6f3344423a253754888bcebb)

- **作者**: hac17
- **时间**: 2026-10-24T16:48:53Z
- **提交信息**: [CI/Build][ROCm] Select qualified ROCm tests in AMD CI (#9320)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0f79bd8](https://github.com/vllm-project/vllm-omni/commit/0f79bd8b0e5ff9379a9a38e0c585db8f8335bf7c)

- **作者**: ZhIMQ
- **时间**: 2026-10-24T14:09:46Z
- **提交信息**: [Bugfix][Qwen-Image-2.1] Snap the trailing VAE tile so tiled decode leaves no seam (#8868)

Signed-off-by: ZhIMQ <15000371166@163.com>

### [a72c51e](https://github.com/vllm-project/vllm-omni/commit/a72c51e022076d6397e16a20c3c619ea4f9e00b1)

- **作者**: shykoe
- **时间**: 2026-10-24T14:03:44Z
- **提交信息**: [Frontend] MiniMax-H3: Add timeline guides to the ComfyUI extension (GUIDE-02) (#9152)

Signed-off-by: shykoe <shykoe@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e900011](https://github.com/vllm-project/vllm-omni/commit/e900011d59319592c6d0451e67b093ae3bde422e)

- **作者**: Yufeng He
- **时间**: 2026-10-24T13:41:14Z
- **提交信息**: [Bugfix] Keep diffusion LoRA buffers resident on the compute device (#8874)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>

### [7cbc776](https://github.com/vllm-project/vllm-omni/commit/7cbc776c16a39f73978ae5ce400729d94e0fda35)

- **作者**: Dong1017
- **时间**: 2026-10-24T10:21:44Z
- **提交信息**: [Bugfix] MiniMax-H3: warn on TaylorSeer order>=2 and document the Ref2VA artifact margin (#9270)

Signed-off-by: GUOGUO <xwdong1998@163.com>

### [517dfa8](https://github.com/vllm-project/vllm-omni/commit/517dfa8cbd905133ca422182a3411231dd7bd0a7)

- **作者**: YAN YIXIN
- **时间**: 2026-10-24T10:18:25Z
- **提交信息**: [Frontend] ComfyUI: add MiniMax-H3 supplied-audio music video workflow (H3-03) (#9226)

Signed-off-by: nikiwang-125 <yixinyan79@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

### [1edbb9e](https://github.com/vllm-project/vllm-omni/commit/1edbb9e80c90adba2394c964441a90aa8f724469)

- **作者**: andyluo7
- **时间**: 2026-10-24T09:29:33Z
- **提交信息**: [diffusion][test][ROCm] Make Hunyuan GroupNorm regression detect missing guard (#9276)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: akshatvishu <akshatnayak197@gmail.com>

### [c42398c](https://github.com/vllm-project/vllm-omni/commit/c42398ca14abf7d028124b6e1a891f3201b971d9)

- **作者**: amy-why-3459
- **时间**: 2026-10-24T09:26:16Z
- **提交信息**: [Core] Fail recompute preemption on AR stages that cannot replay their decode state (#9249)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4901885](https://github.com/vllm-project/vllm-omni/commit/49018858be6e741838d478297b73fe1e2792904f)

- **作者**: Yash Jain
- **时间**: 2026-10-24T07:08:42Z
- **提交信息**: [Kernel] Split the fused GroupNorm+SiLU reduction across CTAs (#6662)

Signed-off-by: Yash Jain <yashjainjain1704@gmail.com>

---
