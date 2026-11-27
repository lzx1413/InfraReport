# GitHub Stars 合并报告 - 2026-11-26

**合并日期**: 2026-11-27
**监控日期**: 2026-11-26
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


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2306
- **最后更新**: 2026-11-26T06:49:55Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: NancyFyong, Bin Jia, Coach257

## AI分析总结

## VeOmni 昨日提交分析（共 6 条）

### 1. 主要更新类型
以**功能新增**为主（4 条），辅以 **Bug 修复**（1 条）与**版本发布**（1 条），整体属于典型的"能力扩展 + 稳定性打磨"批次。

### 2. 关键变更点与项目方向的关系
- **DeepSeek-V4 上下文并行迁移到 NPU（CANN DSA 算子）**：将大模型长上下文训练的分布式并行能力从 GPU 拓展到国产 NPU 生态，直接呼应项目"Model-Centric Distributed Recipe Zoo"的定位——为不同硬件提供可复用的分布式配方。
- **SeedOmni 按模块粒度门控 torch.compile**：把编译优化从全局开关细化到模块级，兼顾性能与训练稳定性。
- **新增 MiniMax H3-Image T2I 微调**：扩展到文生图（图像生成）这一新模态，是"Any Modality"口号的直接落地。
- **liger-kernel 7 元组交叉熵返回兼容修复**：解决第三方算子库版本迭代带来的接口不匹配。
- **Frozen PLE 导出（可选）**：支持冻结参数的可学习专家（PLE）模块导出，服务于 MoE 类模型的检查点管理与复用。
- **v0.1.14 发布**：将上述能力固化为正式版本。

### 3. 对项目的影响与潜在意义
- **硬件多元化**：NPU 适配显著降低对单一硬件的依赖，增强在国产算力环境的可用性，扩大潜在用户群。
- **模态覆盖度提升**：T2I 微调的加入使 VeOmni 从"多模态理解/对话"进一步覆盖"多模态生成"，强化其作为全模态训练底座的竞争力。
- **工程成熟度**：编译粒度控制、算子兼容修复、PLE 导出等属于"生产级细节"，表明项目正从功能铺开转向可用性与鲁棒性打磨。

### 4. 值得关注的技术点
- **CANN DSA 算子**在上下文并行中的应用，是 NPU 上高效支持长序列训练的关键，值得跟踪其与 GPU 实现的性能对比。
- **模块级 torch.compile 门控**的实现机制（如何判定可编译模块、如何规避动态形状问题）对大规模训练调优有参考价值。
- **Frozen PLE 导出**涉及 MoE 模型在推理/部署侧的参数切分策略，与模型部署链路衔接紧密。
- **liger-kernel 7 元组返回**的修复反映了多版本依赖管理这一多模态训练框架的常见痛点。

### 5. 对项目发展的整体影响
VeOmni 的目标是构建覆盖任意模态、任意硬件的分布式训练配方库。本批提交从三个维度推进该目标：**横向上**扩展硬件（NPU）与模态（T2I），**纵向上**深化分布式并行与 MoE 支持，**底座上**修复兼容性问题并发布稳定版本。这种"广度 + 深度 + 稳定性"并进的节奏，说明项目已进入相对成熟的迭代期，正通过持续吸纳新模型架构（DeepSeek-V4、MiniMax H3）来保持配方库的时效性，从而巩固其作为开源多模态训练基础设施的地位。

## 详细提交记录

### [303f007](https://github.com/ByteDance-Seed/VeOmni/commit/303f007f3b4c30e57bba0f2f292fc036378dd8aa)

- **作者**: 帅喆
- **时间**: 2026-11-26T11:33:51Z
- **提交信息**: [ops, model, parallel] feat: run DeepSeek-V4 context parallelism on NPU with the CANN DSA ops (#1477)

### [07f9b91](https://github.com/ByteDance-Seed/VeOmni/commit/07f9b91a99f6ea1791d608e756eba50c496ea086)

- **作者**: Coach257
- **时间**: 2026-11-26T07:14:01Z
- **提交信息**: [omni, dist, model] feat: gate torch.compile per module in SeedOmni (#1486)

### [428b36e](https://github.com/ByteDance-Seed/VeOmni/commit/428b36e1ff84f1723c83cc0ad355dea6bb36b6f8)

- **作者**: NancyFyong
- **时间**: 2026-11-26T06:06:11Z
- **提交信息**: [model, data, ckpt, config] feat: add MiniMax H3-Image T2I fine-tuning (#1481)

### [8dc1963](https://github.com/ByteDance-Seed/VeOmni/commit/8dc1963ca45b60e22d960149b1217c34f359bf2d)

- **作者**: Bin Jia
- **时间**: 2026-11-26T04:01:01Z
- **提交信息**: [release] chore: release v0.1.14 (#1503)

### [5441b8f](https://github.com/ByteDance-Seed/VeOmni/commit/5441b8f4a2ab985cb0f8e8f20a493c64f02ed3d4)

- **作者**: Haojun Zhao
- **时间**: 2026-11-26T03:50:50Z
- **提交信息**: [ops] fix: support liger-kernel 7-tuple cross-entropy forward return (#1500)

### [3336c40](https://github.com/ByteDance-Seed/VeOmni/commit/3336c403bc86e68927bbc1259571402333e0facb)

- **作者**: Joel
- **时间**: 2026-11-26T03:31:48Z
- **提交信息**: [model, ckpt, dist, docs] feat: add opt-in frozen PLE export (#1497)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3029
- **最后更新**: 2026-11-26T10:06:55Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Chernobyllight, Bilang ZHANG, XHPlus

## AI分析总结

## 1. 主要更新类型
- **功能新增**（占主导）：两个大型音频生成能力集成——Seed-VC 音色转换（#1758）与 YuE2 文生音频（#1755），以及 LongCat-Video-Avatar 推理优化（#1762）。
- **Bug修复/硬件适配**：Intel XPU 在 B70 设备上的修复与更新（#1763）。

## 2. 关键变更点及与项目方向的关系
- **音频模态全面扩展**：Seed-VC 与 YuE2 均通过统一的 LightX2V CLI 和 HTTP server 接入，复用项目既有的 DiT、采样器、VAE 算子与部署配置体系，说明 LightX2V 正从纯视频推理框架走向**统一的多模态（视频+音频）推理平台**。
- **部署优化贯穿始终**：两个音频集成都支持 CPU offload、多卡张量并行、编译与启动预热，与项目轻量化、高效推理的核心定位一致。
- **Intel B70 适配**：SP4 四卡并行带来约 3.5× 端到端加速，体现项目持续拓宽硬件后端覆盖（不止 NVIDIA）。

## 3. 对项目的影响和潜在意义
- 音频能力的加入使 LightX2V 可覆盖"图/视频 + 音频"的完整生成链路（如数字人、配音、歌唱转换），显著扩展应用场景。
- 统一 CLI/HTTP 入口降低了新模型接入的边际成本，为后续更多模型的"插件式"集成建立了范式。
- Intel B70 性能数据公开，增强对国产/替代硬件生态的吸引力。

## 4. 值得关注的技术点
- **架构一致性**：Seed-VC（声学转换 + BigVGAN 解码）与 YuE2（AR 语义生成 + NAR 声学生成 + 中点调度器）均遵循"算子复用 + 标准部署配置"的接入模式。
- **验证严谨**：提交含多卡 vs 单卡波形 RMSE、哈希一致性、预热后编译图数量等量化验证，工程质量高。
- **资源外置策略**：权重、样本数据均放在独立 `lightx2v_examples` 仓库，保持主仓库轻量。
- 多卡并行、编译优化在音频模型上的落地（如 NAR TP2、28 个可编译 block）具有参考价值。

## 5. 对项目发展的影响
结合 README 可知 LightX2V 是 Apache 2.0 许可的轻量多模态推理框架，配套完善文档与 Docker。昨日提交显示项目正沿三条主线推进：**模态扩展**（音频原生集成）、**硬件多元化**（Intel XPU 优化）、**性能深化**（并行/编译/预热）。这使项目从"轻量视频推理工具"升级为"覆盖视频与音频、跨多硬件后端的统一高效推理平台"，生态位更加完整，也为其在数字人、内容创作等综合场景中的落地奠定了基础。

## 详细提交记录

### [c1e33b2](https://github.com/ModelTC/LightX2V/commit/c1e33b28753ed18ff306bd95a72121d0dfd4cd74)

- **作者**: XHPlus
- **时间**: 2026-11-26T17:10:10Z
- **提交信息**: [intel xpu] fix and update for B70 device (#1763)

Wan2.1-T2V-1.3B on Intel B70 GPU, 16 fps, 50 steps:



  | SP4 (4 cards) | 1 card | Speedup
-- | -- | -- | --
DiT time per step (mean of 50) | 2.20 s | 8.01 s | 3.6×
DiT total | 122 s | 421 s | 3.5×
T5 text encoding | 8 s | 41 s |  
VAE decode | 9 s | 12 s |  
Whole run | 131 s | 463 s | 3.5×

### [1e91200](https://github.com/ModelTC/LightX2V/commit/1e91200665fa31a14717946515c0d9bfc73bc39c)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-26T12:07:38Z
- **提交信息**: feat: add optimized LongCat-Video-Avatar 1.6 inference (#1762)

### [d9b1099](https://github.com/ModelTC/LightX2V/commit/d9b1099d4f586c68de3c745b2d966f2f5c966255)

- **作者**: Chernobyllight
- **时间**: 2026-11-26T05:24:53Z
- **提交信息**: feat: add native Seed-VC audio conversion (#1758)

Add Seed-VC V1 audio conversion through the standard LightX2V CLI and
HTTP server. Prepared source and reference features produce complete
playable WAV/FLAC audio through a native length regulator, DiT, CFM
sampler and BigVGAN decoder.

## Changes

- Support 44.1 kHz F0-conditioned singing conversion, 22.05 kHz speech
conversion and fixed adapters in the local `seed-vc-lora-v1` format.
- Support block CPU offload, two-GPU tensor parallel inference, DiT
compilation and startup warmup. Inference uses FP32 and PyTorch SDPA.
- Include BigVGAN inference so decoding does not depend on a neighboring
application checkout.
- Provide six numbered presets, CLI and HTTP launchers, deployment
configurations and English/Chinese documentation.
- Store all prepared samples in the sibling
`lightx2v_examples/a2a/seedvc/` checkout. Launchers, default warmup and
HTTP examples use that location. Document sparse checkout for
downloading only the Seed-VC inputs.

Sample dependency: https://github.com/ModelTC/lightx2v_examples/pull/3
must merge before the README's checkout commands work on the examples
repository's `main` branch. The LightX2V commit contains no sample
binaries or manifests, adds no download script, and leaves `.gitignore`
unchanged. Model weights and the private LoRA adapter remain external.
This integration is independent of YuE2.

## Validation

- `pre-commit run --all-files`, shell syntax and staged-diff checks
passed.
- All ten relocated audio/feature files retain their SHA256 hashes and
all manifest references resolve. The three manifests omit the unused
`upstream_commit` field; sample loading succeeds with identical feature
tensors.
- All six CLI presets produced finite, non-silent audio on H100 with
PyTorch 2.8.0+cu128, sample-for-sample identical to the outputs before
relocation.
- Two-GPU inference passed; waveform RMSE against the single-GPU
baseline was 2.20e-5.
- Compilation and default startup warmup used the external samples
successfully; waveform RMSE against eager inference was 3.09e-6.
- An HTTP request using the external sample path produced audio
identical to the CLI baseline.

The PR remains a single commit on the current main branch, with the
sample files removed from that commit rather than deleted in a later
commit. The model registry retains the YuE2 entry already merged into
main alongside Seed-VC; no YuE2 changes are included in this PR. After
rebasing, pre-commit and the SVC, VC and LoRA inference paths were
rechecked with identical audio outputs.

### [239537f](https://github.com/ModelTC/LightX2V/commit/239537fc25f7af9829e756bfd553ae50b376addb)

- **作者**: Chernobyllight
- **时间**: 2026-11-26T03:56:56Z
- **提交信息**: feat: add native YuE2 audio generation (#1755)

Add native YuE2-3B text-to-audio inference through the shared LightX2V
CLI and HTTP server. Requests can supply lyrics, style and optional ABC
notation, then receive 48 kHz stereo FLAC/WAV audio.

## Changes

- Register `yue2 / t2a` with a lightweight request spec and checkpoint
configuration loader.
- Implement optional ABC planning, autoregressive semantic generation
and non-autoregressive acoustic generation using LightX2V operators,
with a midpoint scheduler and the compatible upstream audio VAE decoder.
- Support block CPU offload, two-device NAR tensor parallelism, NAR
compilation and startup warmup. AR remains eager; rank zero samples and
decodes audio.
- Provide four deployment configurations, CLI/server launch scripts, an
HTTP client and bilingual documentation.
- Include one small shared input dataset for 13 end-to-end examples:
Chinese/English generation, prepared or generated scores, style changes,
score editing, instrumental generation and arrangement.

## Validation

- `pre-commit run --all-files`, Bash syntax and general/model-specific
CLI help checks.
- All 13 examples produced finite, non-silent 48 kHz stereo audio on
H100 with the existing SenseNova environment (PyTorch 2.8.0+cu128).
- Repeated seeded requests and separate CPU-offload, TP2 and
compile/warmup runs passed. Compilation retained 28 NAR block callables
and two graphs after startup warmup.
- The final core cleanup passed 17 same-mode before/after comparisons
with identical decoded PCM and FLAC hashes; request validation retained
rejection of 22 invalid cases.
- Formatting changes preserve all 13 assembled requests and their CLI
arguments exactly.

Weights and generated audio are external to the repository. The
integration targets YuE2-3B AR/NAR checkpoints; preprocessing such as
transcription and source separation stays in the application layer.
Combined deployment optimizations are outside the supplied
configurations' validation scope.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2346
- **最后更新**: 2026-11-26T14:19:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 7014
- **最后更新**: 2026-11-27T01:05:45Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 9
- **主要提交者**: eigen, Brian K. Ryu, Adrian

## AI分析总结

# FlashInfer 近期提交分析

## 1. 主要更新类型

- **性能优化**（约 7 项）：集中在 "Cake" 后端的 MLA 解码、Gated Delta Product（GDP）解码、MoE GEMM 与原生 Transformer 解码路径。
- **功能新增**（2 项）：batch-invariant 注意力的 LSE 输出与 attention sinks、batch-invariant FP4 MoE 后端。
- **Bug 修复**（3 项）：Lamport all-reduce 大 workspace 下的 64 位偏移溢出、MNNVL 通信测试的过期断言、Windows arm64 CI 下 alternates 文件换行符问题。
- **测试加固/基础设施**（1 项）：PCIe IPC all-reduce 新增可选的有界等待超时机制，避免死锁挂起。

## 2. 关键变更点与项目方向的关系

FlashInfer 的目标是高性能 GPU 推理内核，这批提交紧密围绕这一核心：

- **Cake 后端持续扩张**：FP16 状态池解码、更宽的 BF16 split-KV reducer、`backend="auto"` 自动选择表扩充。Cake 正成为 SM90/SM100/SM103 上 MLA 与 GDP 解码的主力后端，并通过严格基准规则（中位数比值 ≤0.98）逐单元"转正"。
- **解码调度器精调**：D512 GQA 解码允许 Keeps Q64 保留多 wave split fanout，使长 `max_kv_len` 计划提速 8%–25%，正是 vLLM 等引擎的典型用法。
- **MoE 推理优化**：CuTe-DSL MoE GEMM1 的 ClampedRelu2 epilogue 改用 `tanh.approx` 并将 L² 折入输出 scale，GEMM1 提速 4%–16%。
- **batch-invariant 系列补齐**：LSE 输出与 attention sinks 使其可用于反向重计算与 gpt-oss 类模型（head dim 64、128-token 窗口、per-head sinks）；FP4 MoE 新增 NVFP4/MXFP4 权重对后端（SM100/103/107），经显式 `BackendOptions` 选择，不作默认候选。
- **通信与跨平台可靠性**：修复 >1 GiB workspace 的整数溢出；为 PCIe IPC 提供可选超时以解决 CUDA graph 内 rank 崩溃导致的无限自旋；修复 `Path.write_text` 在 Windows 上 CRLF 转换引发的 Git 路径失败。

## 3. 对项目的影响和潜在意义

- 解码吞吐与延迟在 H100、B200、GB300 上获得可量化提升，尤其覆盖长 KV、多头 MLA 与 MTP/GDP 等 DeepSeek 类模型热点路径。
- `backend="auto"` 经受更严的六轮波动检查，自动调优更保守可靠。
- 通信层溢出修复与超时机制直接回应大规模多卡部署中的静默数据错误与挂死问题。
- batch-invariant 路径从推理专用扩展到可训练（LSE 打通前向-反向闭环），并覆盖含 sinks 模型与 4-bit 量化 MoE，逐步构建覆盖注意力与 MoE、兼顾推理与训练的完整栈。
- Windows arm64 CI 修复保障 native 构建稳定性，降低社区贡献门槛。

## 4. 值得关注的技术点

- **SM90 无 `cvt.rs` 的 FP16 舍入**：35 个解码程序用整数算术实现 RNE/Philox 随机舍入，随机舍入在状态快照类负载上带来最高 3.4x 提速。
- **k-aware split-KV reducer**：按 KV tile 实际占用跳过空 split，在短行场景收益最大。
- **有界自旋的编译期开关**：`SpinGuard` 默认编译为空、生成字节级一致的 cubin，超时走独立 JIT 模块，零开销默认值与可选诊断的工程范式值得借鉴。
- **LSE 的位级兼容设计**：base-2 表示、pinned `lg2.approx.ftz`，请求 LSE 不改变任何输出位；`-inf` sink 可逐位复现无 sinks 结果，sinks 在最后一次 chunk merge 后、归一化前插入一次 merge step，与 tiling 和 kernel body 无关。
- **FP4 MoE 复用**：单一 runner/op 加 `Fp4Pair` 描述符服务两对量化格式，量化在 `prepare_weights` 中现场执行。
- **整数溢出传播链**：从 TensorRT-LLM 上游追溯到 FlashInfer 同类隐患，说明与上游内核生态同步很关键。

## 5. 对项目发展的整体影响

FlashInfer 正在两条线上同时推进：一是内核性能的持续极限压榨，通过 Cake 后端统一 MLA/GDP 等新架构解码路径并以严格基准门槛管理质量；二是通信、CI 与 batch-invariant 栈的成熟化，修复静默错误、补上 CI 盲区、增加故障可诊断性并扩展可训练与 4-bit 场景。前者巩固其"最快推理内核库"的定位，后者降低大规模部署的采用门槛，两者结合有助于 FlashInfer 从研究型内核集合演化为可被 vLLM、TensorRT-LLM 等生产框架放心依赖的推理底座。

## 详细提交记录

### [f52a97a](https://github.com/flashinfer-ai/flashinfer/commit/f52a97a818d92e41c94500e49deb6f47a8bce1a9)

- **作者**: eigen
- **时间**: 2026-11-26T20:40:34Z
- **提交信息**: perf(cake_gdp): faster stochastic FP16 state stores for SM90 decode (#10068)

SM90 FP16-pool GDP decode: stochastic-forms siblings of the n=3 l8r4 programs for T=4, 6, 8 and 16 and a scaled-rolled sibling of the n=4 runtime-token-count program, each storing the same bits as its plain program.

### [74fb3fb](https://github.com/flashinfer-ai/flashinfer/commit/74fb3fb8a64cd36b8f4452a5ef1a7f865eef013e)

- **作者**: eigen
- **时间**: 2026-11-26T10:15:09Z
- **提交信息**: perf(mla): backend="auto" offers for more Cake MLA decode units (#10060)

Add _CAKE_MLA_AUTO_OFFERS rows for the units where the Cake decode
measured faster than the faster of tuned CuTe DSL and TRTLLM-GEN on that
device. Each row passes the table's rule (every planned cell of a unit has
at least three rounds, the median ratio is at most 0.98 and every round is
at most 1.00) and a stricter round check: in at most one of six rounds a
cell is above 0.98, or above one minus the round spread of its baseline
when that spread is larger. Rows are listed per device from that device's
measurements only, with the k-aware wide split-KV reducer in place. The
listed rows are unchanged and other units stay unlisted, so
backend="auto" keeps its previous choice there.

### [d0cbb47](https://github.com/flashinfer-ai/flashinfer/commit/d0cbb476cf4041a619523c325109b4d51f2a45f1)

- **作者**: eigen
- **时间**: 2026-11-26T05:41:48Z
- **提交信息**: perf(mla): Cake BF16 split-KV reducer skips empty KV splits in long-KV decode (#10036)

The Cake backend of `trtllm_batch_decode_with_kv_cache_mla` runs
DeepSeek MLA decode on Blackwell. The family has 24 device programs
before and after this PR. The PR replaces one program and adds none. It
delivers a k-aware build of the wide BF16 split-KV reducer, which the
BF16 split-KV route uses when it plans more than 32 KV splits. It loads
and merges only the KV splits that hold KV tiles and skips the empty
ones. Split counts do not change. The PR changes 42 shapes on B200 (KV
length 65536 to 262144; 57, 61 or 64 splits) and 25 shapes on GB300 (KV
length 131072 to 262144; 61 or 64 splits). All of them use batch 1,
q_len 1 and page size 32 or 64. On these shapes, the geomean speedup
against the previous Cake version (FlashInfer main 6046d47f) is 1.003x
on B200 (min 0.984x, max 1.023x) and 1.007x on GB300 (min 0.996x, max
1.027x). Against the fastest non-Cake backend, the geomean is 1.069x on
B200 (min 0.958x, max 1.382x) and 1.042x on GB300 (min 0.949x, max
1.295x). Short rows, which have fewer live KV tiles than splits, gain
the most. Against the previous Cake version their geomean is 1.009x on
B200 (1.006x with sinks) and 1.019x on GB300 (1.018x with sinks).
Uniform rows, with or without sinks, stay at parity: their geomeans are
0.996x to 1.002x, and single rows range from 0.984x to 1.004x. The
`backend="auto"` selection table does not change.

The kernel's other Cake programs serve BF16 page-32/64 decode, the BF16
split-KV route with up to 64 splits and its reducers for up to 32
splits, FP8 page-32 decode, the FP8 page-64 producers and split
reducers, and a generic tail for other shapes; the family ships on
sm_100a (B200) and sm_103a (GB300).

**Table: the Cake backend on every shape this PR changes.** GPUs: NVIDIA
B200 (sm_100a, 148 SMs) and NVIDIA GB300 (sm_103a, 152 SMs). Software:
CUDA 13.5 JIT (nvcc 13.5) and torch 2.14.1+cu130. Every row uses a BF16
KV cache with batch 1, q_len 1 and page size 32 or 64. "KV length" is
the maximum KV length (max_seq_len). "Lengths" gives the sequence-length
pattern: uniform; varied; short, meaning short varied lengths under the
long maximum, so that a row has fewer live KV tiles than splits; "+
sinks" means with attention sinks. "Splits" is the number of planned KV
splits, which this PR does not change. "Previous Cake" is FlashInfer
main 6046d47f. "Fastest non-Cake" is the faster of tuned trtllm-gen and
cute-dsl, measured on the same GPU in the same rounds, with the faster
backend in parentheses. Timing is the CUPTI kernel span over CUDA-graph
replay, with L2 flushed before every iteration. Each value is the median
of the per-round medians over 6 rounds. Speedup = baseline / this PR; >1
means this PR is faster.

| GPU | page size | batch | q_len | KV length | lengths | splits |
previous Cake (us) | fastest non-Cake (us) | this PR (us) | speedup vs
previous Cake | speedup vs fastest non-Cake |
|---|---|---|---|---|---|---|---|---|---|---|---|
| B200 | 32 | 1 | 1 | 65536 | short | 64 | 15.888 | 17.248 (cute-dsl) |
15.536 | 1.023x | 1.110x |
| B200 | 32 | 1 | 1 | 65536 | short + sinks | 64 | 16.032 | 20.768
(cute-dsl) | 15.808 | 1.014x | 1.314x |
| B200 | 32 | 1 | 1 | 65536 | uniform | 64 | 27.088 | 27.776 (cute-dsl)
| 27.168 | 0.997x | 1.022x |
| B200 | 32 | 1 | 1 | 65536 | uniform + sinks | 64 | 27.504 | 38.080
(cute-dsl) | 27.552 | 0.998x | 1.382x |
| B200 | 32 | 1 | 1 | 65536 | varied | 64 | 25.360 | 26.256 (cute-dsl) |
25.280 | 1.003x | 1.039x |
| B200 | 32 | 1 | 1 | 65568 | uniform | 57 | 28.048 | 28.704 (cute-dsl)
| 28.016 | 1.001x | 1.025x |
| B200 | 32 | 1 | 1 | 65568 | varied | 57 | 22.912 | 23.904 (cute-dsl) |
22.848 | 1.003x | 1.046x |
| B200 | 32 | 1 | 1 | 98304 | uniform | 64 | 34.640 | 35.264 (cute-dsl)
| 34.576 | 1.002x | 1.020x |
| B200 | 32 | 1 | 1 | 98304 | varied | 64 | 30.400 | 31.712 (cute-dsl) |
30.304 | 1.003x | 1.046x |
| B200 | 32 | 1 | 1 | 131072 | short | 64 | 18.208 | 19.536 (cute-dsl) |
18.032 | 1.010x | 1.083x |
| B200 | 32 | 1 | 1 | 131072 | short + sinks | 64 | 18.320 | 23.136
(cute-dsl) | 18.376 | 0.997x | 1.259x |
| B200 | 32 | 1 | 1 | 131072 | uniform | 64 | 41.760 | 41.440 (cute-dsl)
| 41.696 | 1.002x | 0.994x |
| B200 | 32 | 1 | 1 | 131072 | uniform + sinks | 64 | 41.536 | 52.912
(trtllm-gen) | 41.792 | 0.994x | 1.266x |
| B200 | 32 | 1 | 1 | 131072 | varied | 64 | 37.888 | 37.616 (cute-dsl)
| 37.824 | 1.002x | 0.995x |
| B200 | 32 | 1 | 1 | 131104 | uniform | 61 | 42.239 | 41.361 (cute-dsl)
| 42.127 | 1.003x | 0.982x |
| B200 | 32 | 1 | 1 | 131104 | varied | 61 | 41.968 | 41.168 (cute-dsl)
| 41.872 | 1.002x | 0.983x |
| B200 | 32 | 1 | 1 | 196608 | uniform | 64 | 55.168 | 54.048 (cute-dsl)
| 55.264 | 0.998x | 0.978x |
| B200 | 32 | 1 | 1 | 196608 | varied | 64 | 36.416 | 36.160 (cute-dsl)
| 36.336 | 1.002x | 0.995x |
| B200 | 32 | 1 | 1 | 262144 | short | 64 | 23.744 | 25.376 (cute-dsl) |
23.712 | 1.001x | 1.070x |
| B200 | 32 | 1 | 1 | 262144 | short + sinks | 64 | 24.040 | 31.904
(cute-dsl) | 23.968 | 1.003x | 1.331x |
| B200 | 32 | 1 | 1 | 262144 | uniform | 64 | 69.864 | 67.728 (cute-dsl)
| 69.888 | 1.000x | 0.969x |
| B200 | 32 | 1 | 1 | 262144 | varied | 64 | 65.696 | 63.072 (cute-dsl)
| 65.840 | 0.998x | 0.958x |
| B200 | 64 | 1 | 1 | 65536 | short | 64 | 16.112 | 17.727 (cute-dsl) |
16.096 | 1.001x | 1.101x |
| B200 | 64 | 1 | 1 | 65536 | short + sinks | 64 | 16.208 | 20.208
(cute-dsl) | 16.128 | 1.005x | 1.253x |
| B200 | 64 | 1 | 1 | 65536 | uniform | 64 | 27.296 | 28.000 (cute-dsl)
| 27.296 | 1.000x | 1.026x |
| B200 | 64 | 1 | 1 | 65536 | varied | 64 | 25.280 | 25.808 (cute-dsl) |
25.040 | 1.010x | 1.031x |
| B200 | 64 | 1 | 1 | 65600 | uniform | 57 | 28.144 | 28.640 (cute-dsl)
| 28.176 | 0.999x | 1.016x |
| B200 | 64 | 1 | 1 | 65600 | varied | 57 | 21.104 | 21.824 (cute-dsl) |
20.896 | 1.010x | 1.044x |
| B200 | 64 | 1 | 1 | 98304 | uniform | 64 | 34.496 | 35.008 (cute-dsl)
| 34.480 | 1.000x | 1.015x |
| B200 | 64 | 1 | 1 | 98304 | varied | 64 | 28.992 | 29.953 (cute-dsl) |
28.928 | 1.002x | 1.035x |
| B200 | 64 | 1 | 1 | 131072 | short | 64 | 17.840 | 18.863 (cute-dsl) |
17.536 | 1.017x | 1.076x |
| B200 | 64 | 1 | 1 | 131072 | short + sinks | 64 | 17.872 | 22.128
(cute-dsl) | 17.504 | 1.021x | 1.264x |
| B200 | 64 | 1 | 1 | 131072 | uniform | 64 | 40.768 | 41.536 (cute-dsl)
| 40.736 | 1.001x | 1.020x |
| B200 | 64 | 1 | 1 | 131072 | varied | 64 | 32.608 | 33.632 (cute-dsl)
| 32.544 | 1.002x | 1.033x |
| B200 | 64 | 1 | 1 | 131136 | uniform | 61 | 41.712 | 41.217 (cute-dsl)
| 41.600 | 1.003x | 0.991x |
| B200 | 64 | 1 | 1 | 131136 | varied | 61 | 35.200 | 35.633 (cute-dsl)
| 35.328 | 0.996x | 1.009x |
| B200 | 64 | 1 | 1 | 196608 | uniform | 64 | 54.640 | 53.712 (cute-dsl)
| 54.928 | 0.995x | 0.978x |
| B200 | 64 | 1 | 1 | 196608 | varied | 64 | 42.256 | 42.496 (cute-dsl)
| 42.304 | 0.999x | 1.005x |
| B200 | 64 | 1 | 1 | 262144 | short | 64 | 26.672 | 27.808 (cute-dsl) |
26.544 | 1.005x | 1.048x |
| B200 | 64 | 1 | 1 | 262144 | short + sinks | 64 | 26.816 | 35.888
(cute-dsl) | 26.832 | 0.999x | 1.338x |
| B200 | 64 | 1 | 1 | 262144 | uniform | 64 | 68.384 | 67.680 (cute-dsl)
| 69.480 | 0.984x | 0.974x |
| B200 | 64 | 1 | 1 | 262144 | varied | 64 | 42.656 | 42.416 (cute-dsl)
| 42.544 | 1.003x | 0.997x |
| GB300 | 32 | 1 | 1 | 131072 | short | 64 | 17.808 | 18.008 (cute-dsl)
| 17.616 | 1.011x | 1.022x |
| GB300 | 32 | 1 | 1 | 131072 | short + sinks | 64 | 17.632 | 22.624
(cute-dsl) | 17.472 | 1.009x | 1.295x |
| GB300 | 32 | 1 | 1 | 131072 | uniform | 64 | 39.712 | 39.856
(cute-dsl) | 39.872 | 0.996x | 1.000x |
| GB300 | 32 | 1 | 1 | 131072 | uniform + sinks | 64 | 40.224 | 50.448
(trtllm-gen) | 40.160 | 1.002x | 1.256x |
| GB300 | 32 | 1 | 1 | 131072 | varied | 64 | 29.216 | 28.768 (cute-dsl)
| 29.024 | 1.007x | 0.991x |
| GB300 | 32 | 1 | 1 | 131104 | uniform | 61 | 40.928 | 39.664
(cute-dsl) | 40.752 | 1.004x | 0.973x |
| GB300 | 32 | 1 | 1 | 131104 | varied | 61 | 30.736 | 30.848 (cute-dsl)
| 30.624 | 1.004x | 1.007x |
| GB300 | 32 | 1 | 1 | 196608 | uniform | 64 | 53.072 | 52.032
(cute-dsl) | 52.928 | 1.003x | 0.983x |
| GB300 | 32 | 1 | 1 | 196608 | varied | 64 | 47.008 | 44.528 (cute-dsl)
| 46.928 | 1.002x | 0.949x |
| GB300 | 32 | 1 | 1 | 262144 | short | 64 | 22.192 | 22.720 (cute-dsl)
| 21.776 | 1.019x | 1.043x |
| GB300 | 32 | 1 | 1 | 262144 | short + sinks | 64 | 22.480 | 28.192
(cute-dsl) | 21.888 | 1.027x | 1.288x |
| GB300 | 32 | 1 | 1 | 262144 | uniform | 64 | 66.560 | 63.416
(cute-dsl) | 66.512 | 1.001x | 0.953x |
| GB300 | 32 | 1 | 1 | 262144 | varied | 64 | 49.680 | 48.544 (cute-dsl)
| 49.648 | 1.001x | 0.978x |
| GB300 | 64 | 1 | 1 | 131072 | short | 64 | 18.368 | 18.880 (cute-dsl)
| 17.904 | 1.026x | 1.055x |
| GB300 | 64 | 1 | 1 | 131072 | short + sinks | 64 | 18.352 | 22.384
(cute-dsl) | 18.000 | 1.020x | 1.244x |
| GB300 | 64 | 1 | 1 | 131072 | uniform | 64 | 39.296 | 39.392
(cute-dsl) | 39.216 | 1.002x | 1.004x |
| GB300 | 64 | 1 | 1 | 131072 | varied | 64 | 34.208 | 33.520 (cute-dsl)
| 34.096 | 1.003x | 0.983x |
| GB300 | 64 | 1 | 1 | 131136 | uniform | 61 | 39.792 | 39.440
(cute-dsl) | 39.936 | 0.996x | 0.988x |
| GB300 | 64 | 1 | 1 | 131136 | varied | 61 | 33.664 | 32.976 (cute-dsl)
| 33.680 | 1.000x | 0.979x |
| GB300 | 64 | 1 | 1 | 196608 | uniform | 64 | 52.320 | 51.536
(cute-dsl) | 52.240 | 1.002x | 0.987x |
| GB300 | 64 | 1 | 1 | 196608 | varied | 64 | 45.872 | 44.128 (cute-dsl)
| 45.536 | 1.007x | 0.969x |
| GB300 | 64 | 1 | 1 | 262144 | short | 64 | 22.016 | 22.496 (cute-dsl)
| 21.616 | 1.019x | 1.041x |
| GB300 | 64 | 1 | 1 | 262144 | short + sinks | 64 | 22.208 | 27.984
(cute-dsl) | 21.856 | 1.016x | 1.280x |
| GB300 | 64 | 1 | 1 | 262144 | uniform | 64 | 65.104 | 62.320
(cute-dsl) | 65.024 | 1.001x | 0.958x |
| GB300 | 64 | 1 | 1 | 262144 | varied | 64 | 63.488 | 62.000 (cute-dsl)
| 63.424 | 1.001x | 0.978x |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved attention results for short and empty sequences in large
split workloads, including when sink values are enabled.
* Padded outputs now consistently use positive zero, preventing
bit-level differences across execution modes.
* Sequence-length changes during graph replay are handled correctly.
Live outputs retain expected accuracy and determinism across full,
partial, short, and empty sequences.
* Wide split workloads now correctly handle rows with fewer key-value
tokens than splits, as well as rows with no key-value tokens.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [c743270](https://github.com/flashinfer-ai/flashinfer/commit/c743270f9d683faa524e115398c974f910a516ad)

- **作者**: feih-nv
- **时间**: 2026-11-26T05:40:26Z
- **提交信息**: test(comm): the custom communicator in the MNNVL tests gathers any object (#10022)

<!-- .github/pull_request_template.md -->

## 📌 Description

`tests/comm/test_mnnvl_custom_comm.py` and
`tests/comm/test_trtllm_mnnvl_allreduce_custom_comm.py` fail every case
on main with `TypeError: Unsupported type for allgather: <class
'tuple'>`. The tests are stale; the library is within its interface.

**Why**

- `CommBackend.allgather` (`flashinfer/comm/abstractions.py`) takes
`Any`.
- Since #6734, `choose_mnnvl_handle_type` in `flashinfer/comm/mnnvl.py`
gathers a tuple `(hostname, reason, cluster_uuid)`.
- Both tests define their own `CustomCommunicator`, whose `allgather`
handled `int` and `bytes` and raised on anything else.
- These files need 2 and 4 GPUs. The unit-test job gives each file one
GPU, so the cases skip there, and the multi-GPU job does not list them,
so the failure never showed in CI.

**What**

- `CustomCommunicator.allgather` in both files gathers any picklable
object with `dist.all_gather_object` and returns a tuple, like
`TorchDistBackend`.

No library change.

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
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: `tests/comm/test_mnnvl_custom_comm.py
tests/comm/test_trtllm_mnnvl_allreduce_custom_comm.py`

GB200, 4-GPU node, CI container (CUDA 13.0), both files:

| | Result |
|---|---|
| main (`05cad9ac4`) | 4 failed, `TypeError` in `allgather` |
| this PR | 4 passed |

CI will not exercise this change: the cases skip with one GPU and the
files are not in the multi-GPU list.

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

- The two files are not added to `SPAWN_MANAGED_TEST_FILES` here. I only
ran them on GB200 and do not know whether they pass or skip cleanly on
every multi-GPU CI platform. Enrolling them is worth doing once that is
known.
- Other backends written against the old `int | bytes` shape of this
test would fail the same way; ones written against `CommBackend` are
unaffected.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Communication tests now cover gathering picklable values and verifying
results are returned as tuples. Coverage includes a wider range of input
types, without expecting unsupported types to raise an explicit error.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e4e029d](https://github.com/flashinfer-ai/flashinfer/commit/e4e029debf92b3e04a1d8e6316319e8d63784595)

- **作者**: feih-nv
- **时间**: 2026-11-26T05:40:09Z
- **提交信息**: fix(comm): compute the Lamport clear sub-buffer offset in 64 bits (#9949)

<!-- .github/pull_request_template.md -->

## 📌 Description

The Lamport all-reduce kernels return wrong sums on a workspace whose
sub-buffer (`comm_size`) is larger than 1 GiB. No error is raised.

**Why**

- The Lamport workspace holds three sub-buffers of `comm_size` bytes.
Each call writes one and clears the one from two calls back, at
`clear_offset * comm_size`.
- That product was computed in `int`. With `clear_offset == 2` it passes
2^31 once `comm_size` exceeds 1 GiB, so the kernel cleared a wrong
address and left the intended sub-buffer with stale data. A later
one-shot call reading that sub-buffer takes the stale values as arrived.
- The data offset on the line above was already widened to `int64_t`;
the clear offset was not.
- `comm_size = world_size * max_token_num * hidden_dim * 2` bytes (4 for
fp32), capped just under 2 GiB by `MAX_COMM_SIZE`, so 1 to 2 GiB is an
accepted configuration. Example: 8 ranks, hidden 8192, `max_token_num`
8192.

**What**

- `trtllm_allreduce_fusion.cuh`, `trtllm_moe_allreduce_fusion.cuh`: the
clear offset is computed in `int64_t`.
- New `tests/comm/test_trtllm_allreduce_fusion_large_workspace.py`: 2
ranks, `comm_size` 1.04 GiB, nine one-shot calls on one workspace with
new inputs on every call, each compared with a PyTorch reference. Two
cases, one per kernel: the plain all-reduce and the MoE finalize
all-reduce. Needs 4.2 GiB per rank and skips without it. Enrolled in the
multi-GPU job.

**Origin**

Found while reading TensorRT-LLM
[#10499](https://github.com/NVIDIA/TensorRT-LLM/pull/10499)
([7d16f3a28](https://github.com/NVIDIA/TensorRT-LLM/commit/7d16f3a28bd61e0d4bce28e789265083266ac025)),
which makes `comm_size` 64-bit upstream. This PR takes only the part
that is wrong in FlashInfer today. It does not lift the 2 GiB cap: the
generated cake all-reduce kernels on the same workspace read `comm_size`
as `int`. Their clear offset is already 64-bit.

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
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets:
`tests/comm/test_trtllm_allreduce_fusion_large_workspace.py
tests/comm/test_trtllm_allreduce_fusion_pdl.py
tests/comm/test_trtllm_moe_allreduce_fusion.py
tests/comm/test_trtllm_moe_allreduce_fusion_finalize.py`

GB200, 4-GPU node, CI container (CUDA 13.0), the new test file:

| Kernel | Without the fix | With the fix |
|---|---|---|
| All-reduce | fails at call 5: 126,669 of 131,072 elements wrong,
largest difference 6.57 | passes |
| MoE finalize all-reduce | fails: `CUDA error: an illegal memory
access` | passes |

Measured at `410bf315c`; the two later commits change only how the test
starts and stops its rank processes. "Without the fix" is the same tree
with the fix commit reverted. A separate run on main with four workspace
sizes (nine all-reduce calls each, 2 ranks): 64 MiB and 0.92 GiB all
correct; 1.04 GiB and 1.83 GiB each have one wrong call per rank, about
112,700 of 131,072 elements.

**Performance: no measurable change.** The fix widens one multiply that
each thread runs once at kernel entry, outside any loop; below 1 GiB the
address it computes is the same as before.

One-shot all-reduce, bf16, hidden 7168, 16 tokens, GB200. Old and new
expression built side by side from one tree and alternated (old, new,
new, old; three rounds), 600 timed calls per run, per-call GPU time on
rank 0:

| Ranks | Old, median per run (us) | New, median per run (us) |
|---|---|---|
| 2 | 47, 46, 46, 57, 61, 46 | 47, 54, 47, 58, 47, 48 |
| 4 | 48, 44, 44, 59, 47, 57 | 58, 58, 43, 64, 62, 44 |

A run of either build settles near 45 us or near 58 us, so the spread
between runs of one build (about 15 us) is far larger than any
difference between the builds. The fastest runs agree to within 1 us (2
ranks: 46 vs 47; 4 ranks: 44 vs 43). 1 and 128 tokens look the same.

The existing MoE finalize test would not show this even on a large
workspace: it passes the same inputs on every call, so stale Lamport
data equals the right answer.

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

- Four commits: test, fix, the MoE finalize case added to the test, and
a retry when the TCPStore port is taken.
- The retry is for this file only. `_get_open_port` binds a free port,
releases it and hands the number to the ranks, so another process can
take it in between; that failed `multi_gpu_test_b200: [cu129]` once on
this PR with `EADDRINUSE`. A rank that cannot bind now exits with a
dedicated code and the case starts over on a new port, up to three
times. Other failures are not retried. About ten other comm test files
use the same port helper and are not changed here.
- The new test allocates about 4.2 GiB per rank and takes about 4
minutes on GB200, most of it workspace setup.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved buffer offset handling for TRT-LLM all-reduce and MoE
finalize operations with large communication workspaces, helping prevent
incorrect offsets when workspace sizes exceed 1 GiB.
* **Tests**
* Added coverage for repeated all-reduce and MoE finalize operations
using large workspaces across two GPUs. The test checks results across
multiple calls and skips when the required GPUs or memory are
unavailable.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [26075a1](https://github.com/flashinfer-ai/flashinfer/commit/26075a1331ff91530706567b59389c23cc143648)

- **作者**: eigen
- **时间**: 2026-11-26T01:57:47Z
- **提交信息**: feat(cake_gdp): FP16 state pool for the decode routes on SM90 (#10039)

`cake_gated_delta_product_mtp` (`flashinfer.cake_gdp`) is the Cake Gated DeltaProduct (GDP) decode kernel, with K = 128, V = 64 and an FP32 or FP16 state pool. It has four routes, one for each number of Householder updates per token, n = 1, 2, 3 and 4. An FP16 pool keeps the recurrence in FP32. It rounds each stored state to FP16: to nearest even (RNE) with `rand_seed=None`, or stochastically with Philox bits when `rand_seed` is given. This PR delivers the FP16 pool on SM90 (`sm_90a`, H100), which has no `cvt.rs`, so its 35 FP16 decode programs round in integer arithmetic. The baseline is the previous Cake version: the same call with an FP32 pool on FlashInfer main, on the same H100, at n = 3. Speedup is FP32 time / FP16 time, so above 1 means FP16 is faster, for R10 (`philox_rounds=10`, default), R5 (`philox_rounds=5`) and RNE.

- Final state only, 144 shapes (heads 80, 24, 20, 10 × batch 1, 16, 64, 256 × T 1 to 8 and 16): R10 1.040x (0.845x..1.726x), R5 1.092x (0.901x..1.886x), RNE 1.213x (0.943x..1.946x). Rows below 1: 55 for R10, 31 for R5 and 3 for RNE. The slowest R10 row is T 1, 10 heads, batch 16: 5.58 us FP32, 6.61 us FP16 (0.845x). The largest absolute R10 cost is T 8, 80 heads, batch 256: 730.46 us FP32, 795.06 us FP16 (0.919x). The slowest RNE row is T 1, 10 heads, batch 1: 2.93 us FP32, 3.10 us FP16 (0.943x).
- State snapshot per token, 64 shapes (same heads and batches, T 2, 4, 8, 16): R10 1.541x (1.012x..2.647x), R5 1.595x (1.062x..2.734x), RNE 1.939x (1.265x..3.397x); no row below 1.
- Runtime token count with a snapshot per token, 12 shapes (T 10 and 12 × batch 16, 64, 256 × heads 80, 20): R10 1.514x (1.248x..1.745x), R5 1.587x (1.359x..1.744x), RNE 2.325x (1.943x..2.653x); no row below 1.
- All 220 shapes: R10 1.190x, R5 1.244x, RNE 1.440x.

The other Cake GDP variants are FP32 decode pools (SM90, SM100, SM103, SM107), FP16 `cvt.rs` decode pools (SM100, SM103, SM107) and chunked varlen prefill (SM90, SM100, SM103); with this PR, decode ships both pool types on `sm_90a`, `sm_100a`, `sm_103a` and `sm_107a`.

Each table below gives, per shape, the median kernel time in microseconds of the same decode call with n = 3, K = 128, V = 64 and BF16 inputs. FP32 state: the FP32 state pool on FlashInfer main (the baseline). FP16 R10 / R5: the FP16 state pool with stochastic rounding, `philox_rounds` 10 (the default) / 5. FP16 RNE: the FP16 state pool rounded to nearest even (no seed). Time: median CUPTI kernel time, cold L2, no CUDA graph, all arms in one process on one GPU, median of 2 passes (each pass the median of 3 x 32 samples per arm). speedup = FP32 time / FP16 time (> 1: FP16 faster).

<details>
<summary>NVIDIA H100 SXM 80GB (HBM3), SM90 (`sm_90a`, 132 SMs), CUDA 13.4: final state only, 144 shapes, median kernel time (us)</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16 R5 (us) | speedup | FP16 RNE (us) | speedup |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 80 | 1 | 4.27 | 4.58 | 0.934 | 4.42 | 0.967 | 4.11 | 1.039 |
| 1 | 80 | 16 | 24.63 | 20.88 | 1.180 | 18.75 | 1.314 | 16.45 | 1.498 |
| 1 | 80 | 64 | 110.81 | 68.72 | 1.612 | 62.67 | 1.768 | 59.02 | 1.878 |
| 1 | 80 | 256 | 454.63 | 263.37 | 1.726 | 241.01 | 1.886 | 233.62 | 1.946 |
| 1 | 24 | 1 | 3.31 | 3.73 | 0.888 | 3.57 | 0.928 | 3.41 | 0.972 |
| 1 | 24 | 16 | 9.39 | 8.45 | 1.112 | 7.55 | 1.244 | 7.12 | 1.319 |
| 1 | 24 | 64 | 31.50 | 23.47 | 1.342 | 21.31 | 1.478 | 18.75 | 1.680 |
| 1 | 24 | 256 | 134.50 | 81.78 | 1.645 | 74.74 | 1.799 | 70.86 | 1.898 |
| 1 | 20 | 1 | 3.26 | 3.68 | 0.885 | 3.58 | 0.908 | 3.33 | 0.978 |
| 1 | 20 | 16 | 8.94 | 8.10 | 1.104 | 7.22 | 1.238 | 6.58 | 1.359 |
| 1 | 20 | 64 | 25.79 | 20.80 | 1.240 | 18.48 | 1.396 | 16.34 | 1.579 |
| 1 | 20 | 256 | 111.68 | 68.71 | 1.625 | 62.96 | 1.774 | 58.98 | 1.893 |
| 1 | 10 | 1 | 2.93 | 3.33 | 0.880 | 3.25 | 0.901 | 3.10 | 0.943 |
| 1 | 10 | 16 | 5.58 | 6.61 | 0.845 | 6.11 | 0.914 | 5.44 | 1.026 |
| 1 | 10 | 64 | 13.47 | 13.58 | 0.992 | 12.18 | 1.106 | 10.79 | 1.248 |
| 1 | 10 | 256 | 54.34 | 36.55 | 1.487 | 32.86 | 1.654 | 29.65 | 1.833 |
| 2 | 80 | 1 | 5.20 | 5.52 | 0.942 | 5.22 | 0.997 | 4.58 | 1.136 |
| 2 | 80 | 16 | 31.28 | 30.37 | 1.030 | 28.62 | 1.093 | 23.75 | 1.317 |
| 2 | 80 | 64 | 118.40 | 102.61 | 1.154 | 95.39 | 1.241 | 77.58 | 1.526 |
| 2 | 80 | 256 | 468.38 | 379.05 | 1.236 | 348.50 | 1.344 | 298.13 | 1.571 |
| 2 | 24 | 1 | 4.70 | 4.46 | 1.054 | 4.26 | 1.105 | 3.86 | 1.220 |
| 2 | 24 | 16 | 12.35 | 11.06 | 1.117 | 10.22 | 1.208 | 8.91 | 1.386 |
| 2 | 24 | 64 | 37.22 | 34.88 | 1.067 | 32.85 | 1.133 | 26.41 | 1.410 |
| 2 | 24 | 256 | 141.78 | 121.04 | 1.171 | 110.98 | 1.277 | 88.94 | 1.594 |
| 2 | 20 | 1 | 4.70 | 4.46 | 1.054 | 4.28 | 1.099 | 3.89 | 1.210 |
| 2 | 20 | 16 | 10.96 | 10.62 | 1.032 | 9.87 | 1.110 | 8.21 | 1.335 |
| 2 | 20 | 64 | 31.02 | 30.06 | 1.032 | 28.43 | 1.091 | 23.52 | 1.319 |
| 2 | 20 | 256 | 118.14 | 101.68 | 1.162 | 93.92 | 1.258 | 74.75 | 1.580 |
| 2 | 10 | 1 | 4.54 | 4.36 | 1.042 | 4.19 | 1.084 | 3.79 | 1.198 |
| 2 | 10 | 16 | 7.47 | 6.78 | 1.101 | 6.32 | 1.182 | 5.44 | 1.374 |
| 2 | 10 | 64 | 19.92 | 17.79 | 1.120 | 16.72 | 1.191 | 14.94 | 1.333 |
| 2 | 10 | 256 | 60.11 | 54.27 | 1.108 | 51.10 | 1.176 | 40.14 | 1.497 |
| 3 | 80 | 1 | 5.98 | 6.29 | 0.952 | 5.98 | 1.000 | 5.35 | 1.118 |
| 3 | 80 | 16 | 35.78 | 34.98 | 1.023 | 33.11 | 1.081 | 28.12 | 1.273 |
| 3 | 80 | 64 | 124.65 | 117.13 | 1.064 | 107.46 | 1.160 | 88.45 | 1.409 |
| 3 | 80 | 256 | 481.65 | 440.79 | 1.093 | 394.74 | 1.220 | 329.17 | 1.463 |
| 3 | 24 | 1 | 5.47 | 5.10 | 1.072 | 4.91 | 1.114 | 4.48 | 1.221 |
| 3 | 24 | 16 | 13.83 | 12.61 | 1.097 | 11.73 | 1.179 | 10.56 | 1.310 |
| 3 | 24 | 64 | 41.81 | 39.53 | 1.058 | 37.42 | 1.117 | 31.24 | 1.338 |
| 3 | 24 | 256 | 148.22 | 138.99 | 1.066 | 126.82 | 1.169 | 103.38 | 1.434 |
| 3 | 20 | 1 | 5.41 | 5.04 | 1.073 | 4.86 | 1.112 | 4.45 | 1.216 |
| 3 | 20 | 16 | 12.42 | 11.36 | 1.093 | 10.66 | 1.165 | 9.20 | 1.350 |
| 3 | 20 | 64 | 35.22 | 34.82 | 1.011 | 32.85 | 1.072 | 27.82 | 1.266 |
| 3 | 20 | 256 | 124.23 | 117.08 | 1.061 | 106.43 | 1.167 | 86.83 | 1.431 |
| 3 | 10 | 1 | 5.36 | 5.01 | 1.070 | 4.86 | 1.104 | 4.43 | 1.209 |
| 3 | 10 | 16 | 8.66 | 7.88 | 1.099 | 7.50 | 1.154 | 6.66 | 1.301 |
| 3 | 10 | 64 | 22.81 | 20.42 | 1.117 | 20.20 | 1.129 | 17.85 | 1.278 |
| 3 | 10 | 256 | 65.08 | 61.65 | 1.056 | 56.99 | 1.142 | 47.15 | 1.380 |
| 4 | 80 | 1 | 6.18 | 6.85 | 0.902 | 6.54 | 0.944 | 5.90 | 1.046 |
| 4 | 80 | 16 | 39.94 | 38.61 | 1.034 | 37.54 | 1.064 | 31.55 | 1.266 |
| 4 | 80 | 64 | 131.82 | 135.42 | 0.973 | 123.92 | 1.064 | 102.69 | 1.284 |
| 4 | 80 | 256 | 494.76 | 505.51 | 0.979 | 456.88 | 1.083 | 379.17 | 1.305 |
| 4 | 24 | 1 | 5.62 | 5.20 | 1.080 | 5.01 | 1.121 | 4.59 | 1.223 |
| 4 | 24 | 16 | 15.15 | 14.06 | 1.077 | 13.12 | 1.155 | 11.78 | 1.287 |
| 4 | 24 | 64 | 46.66 | 44.52 | 1.048 | 42.21 | 1.105 | 35.36 | 1.319 |
| 4 | 24 | 256 | 154.50 | 159.90 | 0.966 | 146.10 | 1.057 | 120.46 | 1.283 |
| 4 | 20 | 1 | 5.60 | 5.20 | 1.077 | 5.01 | 1.118 | 4.58 | 1.224 |
| 4 | 20 | 16 | 13.63 | 12.50 | 1.091 | 11.78 | 1.158 | 10.48 | 1.301 |
| 4 | 20 | 64 | 39.46 | 38.34 | 1.029 | 36.77 | 1.073 | 31.07 | 1.270 |
| 4 | 20 | 256 | 130.66 | 134.96 | 0.968 | 122.86 | 1.063 | 101.14 | 1.292 |
| 4 | 10 | 1 | 5.55 | 5.12 | 1.084 | 4.93 | 1.127 | 4.56 | 1.218 |
| 4 | 10 | 16 | 9.60 | 8.61 | 1.115 | 8.27 | 1.161 | 7.38 | 1.302 |
| 4 | 10 | 64 | 25.02 | 22.26 | 1.124 | 21.20 | 1.180 | 19.79 | 1.264 |
| 4 | 10 | 256 | 69.70 | 69.92 | 0.997 | 64.92 | 1.074 | 53.73 | 1.297 |
| 5 | 80 | 1 | 7.06 | 7.47 | 0.944 | 7.30 | 0.967 | 6.58 | 1.073 |
| 5 | 80 | 16 | 48.46 | 44.10 | 1.099 | 41.79 | 1.159 | 38.01 | 1.275 |
| 5 | 80 | 64 | 151.86 | 149.50 | 1.016 | 140.47 | 1.081 | 124.82 | 1.217 |
| 5 | 80 | 256 | 553.90 | 551.89 | 1.004 | 514.78 | 1.076 | 462.69 | 1.197 |
| 5 | 24 | 1 | 6.48 | 7.06 | 0.918 | 6.88 | 0.942 | 6.26 | 1.036 |
| 5 | 24 | 16 | 17.55 | 15.66 | 1.121 | 14.77 | 1.188 | 13.90 | 1.263 |
| 5 | 24 | 64 | 55.80 | 49.86 | 1.119 | 47.29 | 1.180 | 42.67 | 1.308 |
| 5 | 24 | 256 | 178.17 | 175.92 | 1.013 | 164.62 | 1.082 | 148.10 | 1.203 |
| 5 | 20 | 1 | 6.42 | 6.99 | 0.918 | 6.86 | 0.936 | 6.22 | 1.031 |
| 5 | 20 | 16 | 16.06 | 14.29 | 1.124 | 13.66 | 1.175 | 12.40 | 1.295 |
| 5 | 20 | 64 | 47.79 | 43.61 | 1.096 | 41.28 | 1.158 | 37.70 | 1.268 |
| 5 | 20 | 256 | 150.71 | 148.56 | 1.014 | 138.96 | 1.085 | 124.61 | 1.209 |
| 5 | 10 | 1 | 6.35 | 6.93 | 0.917 | 6.78 | 0.936 | 6.21 | 1.023 |
| 5 | 10 | 16 | 10.66 | 10.37 | 1.028 | 9.92 | 1.074 | 9.02 | 1.181 |
| 5 | 10 | 64 | 29.74 | 27.30 | 1.090 | 25.76 | 1.155 | 23.84 | 1.248 |
| 5 | 10 | 256 | 81.12 | 77.78 | 1.043 | 72.82 | 1.114 | 65.49 | 1.239 |
| 6 | 80 | 1 | 7.82 | 7.98 | 0.980 | 7.79 | 1.004 | 7.30 | 1.072 |
| 6 | 80 | 16 | 44.74 | 47.47 | 0.942 | 46.02 | 0.972 | 40.19 | 1.113 |
| 6 | 80 | 64 | 151.40 | 165.39 | 0.915 | 156.68 | 0.966 | 135.47 | 1.118 |
| 6 | 80 | 256 | 570.51 | 616.48 | 0.925 | 579.70 | 0.984 | 505.73 | 1.128 |
| 6 | 24 | 1 | 7.17 | 7.18 | 0.998 | 7.07 | 1.014 | 6.64 | 1.080 |
| 6 | 24 | 16 | 17.98 | 17.08 | 1.053 | 16.21 | 1.110 | 14.74 | 1.220 |
| 6 | 24 | 64 | 51.15 | 54.64 | 0.936 | 52.96 | 0.966 | 45.78 | 1.117 |
| 6 | 24 | 256 | 180.27 | 195.74 | 0.921 | 184.91 | 0.975 | 160.46 | 1.123 |
| 6 | 20 | 1 | 7.12 | 7.20 | 0.989 | 7.06 | 1.009 | 6.64 | 1.072 |
| 6 | 20 | 16 | 16.96 | 16.67 | 1.017 | 15.71 | 1.079 | 14.22 | 1.192 |
| 6 | 20 | 64 | 44.07 | 47.42 | 0.929 | 45.46 | 0.970 | 39.68 | 1.111 |
| 6 | 20 | 256 | 151.54 | 165.42 | 0.916 | 156.26 | 0.970 | 135.23 | 1.121 |
| 6 | 10 | 1 | 7.04 | 7.10 | 0.991 | 6.96 | 1.012 | 6.56 | 1.073 |
| 6 | 10 | 16 | 11.92 | 11.57 | 1.030 | 11.22 | 1.063 | 10.38 | 1.148 |
| 6 | 10 | 64 | 27.49 | 27.68 | 0.993 | 26.42 | 1.041 | 25.46 | 1.080 |
| 6 | 10 | 256 | 79.60 | 86.92 | 0.916 | 82.03 | 0.970 | 71.25 | 1.117 |
| 7 | 80 | 1 | 8.54 | 8.72 | 0.980 | 8.47 | 1.008 | 8.03 | 1.064 |
| 7 | 80 | 16 | 52.50 | 48.69 | 1.078 | 47.25 | 1.111 | 43.25 | 1.214 |
| 7 | 80 | 64 | 169.72 | 171.06 | 0.992 | 165.55 | 1.025 | 152.74 | 1.111 |
| 7 | 80 | 256 | 633.33 | 647.90 | 0.978 | 626.26 | 1.011 | 578.32 | 1.095 |
| 7 | 24 | 1 | 7.86 | 7.74 | 1.014 | 7.60 | 1.034 | 7.13 | 1.102 |
| 7 | 24 | 16 | 19.74 | 17.49 | 1.129 | 16.90 | 1.169 | 15.92 | 1.240 |
| 7 | 24 | 64 | 59.93 | 56.59 | 1.059 | 54.74 | 1.095 | 50.21 | 1.194 |
| 7 | 24 | 256 | 200.23 | 203.26 | 0.985 | 196.32 | 1.020 | 181.38 | 1.104 |
| 7 | 20 | 1 | 7.79 | 7.73 | 1.008 | 7.58 | 1.027 | 7.14 | 1.092 |
| 7 | 20 | 16 | 18.29 | 16.86 | 1.084 | 16.32 | 1.121 | 15.39 | 1.188 |
| 7 | 20 | 64 | 52.61 | 48.66 | 1.081 | 47.25 | 1.113 | 43.40 | 1.212 |
| 7 | 20 | 256 | 169.74 | 171.20 | 0.991 | 165.50 | 1.026 | 152.75 | 1.111 |
| 7 | 10 | 1 | 7.73 | 7.65 | 1.010 | 7.51 | 1.029 | 7.09 | 1.090 |
| 7 | 10 | 16 | 13.07 | 12.37 | 1.057 | 11.92 | 1.097 | 10.99 | 1.189 |
| 7 | 10 | 64 | 33.08 | 30.99 | 1.067 | 30.16 | 1.097 | 27.54 | 1.201 |
| 7 | 10 | 256 | 91.02 | 90.09 | 1.010 | 86.94 | 1.047 | 79.58 | 1.144 |
| 8 | 80 | 1 | 8.86 | 9.38 | 0.945 | 9.09 | 0.975 | 8.37 | 1.059 |
| 8 | 80 | 16 | 57.18 | 57.94 | 0.987 | 55.64 | 1.028 | 49.76 | 1.149 |
| 8 | 80 | 64 | 194.52 | 209.56 | 0.928 | 198.74 | 0.979 | 178.45 | 1.090 |
| 8 | 80 | 256 | 730.46 | 795.06 | 0.919 | 760.11 | 0.961 | 683.47 | 1.069 |
| 8 | 24 | 1 | 8.24 | 8.05 | 1.024 | 7.89 | 1.045 | 7.46 | 1.105 |
| 8 | 24 | 16 | 21.73 | 20.85 | 1.042 | 19.89 | 1.093 | 18.25 | 1.191 |
| 8 | 24 | 64 | 64.94 | 67.42 | 0.963 | 65.12 | 0.997 | 58.15 | 1.117 |
| 8 | 24 | 256 | 229.98 | 247.80 | 0.928 | 236.57 | 0.972 | 212.41 | 1.083 |
| 8 | 20 | 1 | 8.26 | 8.02 | 1.030 | 7.87 | 1.049 | 7.44 | 1.110 |
| 8 | 20 | 16 | 20.54 | 20.40 | 1.007 | 19.41 | 1.059 | 17.68 | 1.162 |
| 8 | 20 | 64 | 57.04 | 58.16 | 0.981 | 55.74 | 1.023 | 49.83 | 1.145 |
| 8 | 20 | 256 | 194.39 | 208.79 | 0.931 | 198.80 | 0.978 | 178.74 | 1.088 |
| 8 | 10 | 1 | 8.22 | 7.94 | 1.036 | 7.78 | 1.058 | 7.36 | 1.117 |
| 8 | 10 | 16 | 13.44 | 13.28 | 1.012 | 12.83 | 1.047 | 11.97 | 1.123 |
| 8 | 10 | 64 | 35.42 | 33.31 | 1.063 | 34.63 | 1.023 | 31.52 | 1.124 |
| 8 | 10 | 256 | 102.53 | 108.66 | 0.944 | 104.24 | 0.984 | 93.04 | 1.102 |
| 16 | 80 | 1 | 14.05 | 14.38 | 0.977 | 14.08 | 0.998 | 13.71 | 1.025 |
| 16 | 80 | 16 | 95.25 | 95.75 | 0.995 | 94.25 | 1.011 | 89.34 | 1.066 |
| 16 | 80 | 64 | 333.35 | 341.30 | 0.977 | 334.11 | 0.998 | 320.48 | 1.040 |
| 16 | 80 | 256 | 1278.45 | 1321.52 | 0.967 | 1290.62 | 0.991 | 1240.46 | 1.031 |
| 16 | 24 | 1 | 13.07 | 12.70 | 1.029 | 12.54 | 1.042 | 12.26 | 1.067 |
| 16 | 24 | 16 | 33.63 | 32.59 | 1.032 | 31.94 | 1.053 | 30.98 | 1.086 |
| 16 | 24 | 64 | 111.15 | 111.90 | 0.993 | 110.03 | 1.010 | 104.64 | 1.062 |
| 16 | 24 | 256 | 396.79 | 407.36 | 0.974 | 398.54 | 0.996 | 382.10 | 1.038 |
| 16 | 20 | 1 | 13.04 | 12.69 | 1.028 | 12.53 | 1.041 | 12.19 | 1.070 |
| 16 | 20 | 16 | 32.44 | 31.94 | 1.016 | 31.12 | 1.042 | 30.05 | 1.080 |
| 16 | 20 | 64 | 95.06 | 95.47 | 0.996 | 93.80 | 1.013 | 88.98 | 1.068 |
| 16 | 20 | 256 | 332.80 | 341.42 | 0.975 | 333.98 | 0.996 | 320.03 | 1.040 |
| 16 | 10 | 1 | 13.02 | 12.58 | 1.035 | 12.40 | 1.050 | 12.13 | 1.073 |
| 16 | 10 | 16 | 24.16 | 21.01 | 1.150 | 20.70 | 1.167 | 20.16 | 1.198 |
| 16 | 10 | 64 | 59.49 | 59.95 | 0.992 | 58.94 | 1.009 | 55.90 | 1.064 |
| 16 | 10 | 256 | 176.66 | 180.05 | 0.981 | 176.39 | 1.002 | 168.35 | 1.049 |

</details>

<details>
<summary>NVIDIA H100 SXM 80GB (HBM3), SM90 (`sm_90a`, 132 SMs), CUDA 13.4: a state snapshot per token, 64 shapes, median kernel time (us)</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16 R5 (us) | speedup | FP16 RNE (us) | speedup |
|---|---|---|---|---|---|---|---|---|---|
| 2 | 80 | 1 | 6.03 | 5.96 | 1.012 | 5.68 | 1.062 | 4.77 | 1.265 |
| 2 | 80 | 16 | 47.41 | 33.50 | 1.415 | 32.88 | 1.442 | 27.73 | 1.710 |
| 2 | 80 | 64 | 180.46 | 115.44 | 1.563 | 109.35 | 1.650 | 96.06 | 1.879 |
| 2 | 80 | 256 | 715.36 | 436.50 | 1.639 | 407.89 | 1.754 | 368.11 | 1.943 |
| 2 | 24 | 1 | 5.33 | 4.85 | 1.099 | 4.67 | 1.140 | 4.00 | 1.332 |
| 2 | 24 | 16 | 15.40 | 12.85 | 1.199 | 11.94 | 1.290 | 9.58 | 1.608 |
| 2 | 24 | 64 | 55.71 | 39.70 | 1.403 | 38.74 | 1.438 | 31.13 | 1.790 |
| 2 | 24 | 256 | 216.24 | 138.05 | 1.566 | 130.03 | 1.663 | 114.08 | 1.896 |
| 2 | 20 | 1 | 5.33 | 4.86 | 1.095 | 4.67 | 1.140 | 4.00 | 1.332 |
| 2 | 20 | 16 | 13.87 | 12.46 | 1.113 | 11.55 | 1.201 | 8.91 | 1.557 |
| 2 | 20 | 64 | 47.26 | 33.41 | 1.415 | 32.43 | 1.457 | 27.29 | 1.732 |
| 2 | 20 | 256 | 180.64 | 115.50 | 1.564 | 109.38 | 1.652 | 96.17 | 1.878 |
| 2 | 10 | 1 | 5.31 | 4.82 | 1.103 | 4.62 | 1.149 | 3.98 | 1.333 |
| 2 | 10 | 16 | 9.60 | 7.60 | 1.263 | 7.22 | 1.330 | 5.73 | 1.676 |
| 2 | 10 | 64 | 26.22 | 19.55 | 1.341 | 18.50 | 1.418 | 16.08 | 1.631 |
| 2 | 10 | 256 | 91.34 | 61.06 | 1.496 | 58.59 | 1.559 | 51.14 | 1.786 |
| 4 | 80 | 1 | 20.42 | 8.14 | 2.507 | 7.81 | 2.615 | 6.64 | 3.075 |
| 4 | 80 | 16 | 79.48 | 52.76 | 1.506 | 50.19 | 1.584 | 43.50 | 1.827 |
| 4 | 80 | 64 | 309.90 | 191.34 | 1.620 | 182.22 | 1.701 | 158.82 | 1.951 |
| 4 | 80 | 256 | 1234.63 | 730.06 | 1.691 | 693.69 | 1.780 | 626.18 | 1.972 |
| 4 | 24 | 1 | 16.10 | 6.08 | 2.647 | 5.89 | 2.734 | 4.74 | 3.393 |
| 4 | 24 | 16 | 23.27 | 19.23 | 1.210 | 18.30 | 1.271 | 13.63 | 1.707 |
| 4 | 24 | 64 | 94.86 | 62.19 | 1.525 | 59.12 | 1.605 | 49.83 | 1.904 |
| 4 | 24 | 256 | 374.15 | 227.38 | 1.646 | 216.46 | 1.728 | 190.19 | 1.967 |
| 4 | 20 | 1 | 16.09 | 6.10 | 2.639 | 5.89 | 2.732 | 4.74 | 3.397 |
| 4 | 20 | 16 | 20.96 | 16.62 | 1.261 | 15.89 | 1.319 | 11.49 | 1.825 |
| 4 | 20 | 64 | 79.78 | 52.59 | 1.517 | 50.17 | 1.590 | 42.94 | 1.858 |
| 4 | 20 | 256 | 312.06 | 191.33 | 1.631 | 182.43 | 1.711 | 158.86 | 1.964 |
| 4 | 10 | 1 | 15.32 | 6.00 | 2.553 | 5.81 | 2.638 | 4.70 | 3.257 |
| 4 | 10 | 16 | 13.78 | 11.06 | 1.246 | 10.56 | 1.305 | 7.87 | 1.750 |
| 4 | 10 | 64 | 41.05 | 29.42 | 1.395 | 28.06 | 1.463 | 24.27 | 1.691 |
| 4 | 10 | 256 | 156.82 | 100.26 | 1.564 | 95.32 | 1.645 | 80.93 | 1.938 |
| 8 | 80 | 1 | 17.45 | 13.20 | 1.322 | 12.88 | 1.355 | 9.44 | 1.848 |
| 8 | 80 | 16 | 142.67 | 95.18 | 1.499 | 92.22 | 1.547 | 76.38 | 1.868 |
| 8 | 80 | 64 | 570.98 | 347.71 | 1.642 | 336.30 | 1.698 | 290.85 | 1.963 |
| 8 | 80 | 256 | 2287.56 | 1350.98 | 1.693 | 1302.84 | 1.756 | 1159.29 | 1.973 |
| 8 | 24 | 1 | 16.62 | 9.84 | 1.689 | 9.66 | 1.720 | 7.60 | 2.187 |
| 8 | 24 | 16 | 40.67 | 32.34 | 1.258 | 31.34 | 1.298 | 21.92 | 1.855 |
| 8 | 24 | 64 | 171.37 | 113.14 | 1.515 | 109.58 | 1.564 | 88.26 | 1.942 |
| 8 | 24 | 256 | 688.26 | 415.69 | 1.656 | 401.90 | 1.712 | 351.18 | 1.960 |
| 8 | 20 | 1 | 16.40 | 9.82 | 1.669 | 9.63 | 1.703 | 7.55 | 2.172 |
| 8 | 20 | 16 | 37.01 | 31.73 | 1.166 | 30.68 | 1.206 | 21.08 | 1.756 |
| 8 | 20 | 64 | 143.38 | 95.30 | 1.505 | 92.38 | 1.552 | 76.67 | 1.870 |
| 8 | 20 | 256 | 574.12 | 348.02 | 1.650 | 336.44 | 1.706 | 292.94 | 1.960 |
| 8 | 10 | 1 | 15.74 | 9.71 | 1.621 | 9.54 | 1.651 | 7.49 | 2.103 |
| 8 | 10 | 16 | 26.80 | 18.24 | 1.469 | 17.78 | 1.507 | 12.86 | 2.083 |
| 8 | 10 | 64 | 72.42 | 50.54 | 1.433 | 48.99 | 1.478 | 41.98 | 1.725 |
| 8 | 10 | 256 | 287.61 | 182.67 | 1.574 | 176.77 | 1.627 | 148.02 | 1.943 |
| 16 | 80 | 1 | 37.71 | 20.27 | 1.860 | 20.00 | 1.886 | 16.35 | 2.306 |
| 16 | 80 | 16 | 271.82 | 177.42 | 1.532 | 174.60 | 1.557 | 139.85 | 1.944 |
| 16 | 80 | 64 | 1093.14 | 656.56 | 1.665 | 645.66 | 1.693 | 560.85 | 1.949 |
| 16 | 80 | 256 | 4391.37 | 2578.59 | 1.703 | 2534.98 | 1.732 | 2248.58 | 1.953 |
| 16 | 24 | 1 | 35.55 | 15.71 | 2.263 | 15.58 | 2.281 | 12.50 | 2.845 |
| 16 | 24 | 16 | 75.55 | 57.47 | 1.315 | 56.43 | 1.339 | 40.55 | 1.863 |
| 16 | 24 | 64 | 324.90 | 210.10 | 1.546 | 207.02 | 1.569 | 166.94 | 1.946 |
| 16 | 24 | 256 | 1313.10 | 786.77 | 1.669 | 774.14 | 1.696 | 674.99 | 1.945 |
| 16 | 20 | 1 | 35.45 | 15.74 | 2.253 | 15.57 | 2.277 | 12.46 | 2.844 |
| 16 | 20 | 16 | 69.86 | 56.74 | 1.231 | 55.86 | 1.251 | 37.94 | 1.841 |
| 16 | 20 | 64 | 272.47 | 177.98 | 1.531 | 174.88 | 1.558 | 140.09 | 1.945 |
| 16 | 20 | 256 | 1097.63 | 656.54 | 1.672 | 645.77 | 1.700 | 563.53 | 1.948 |
| 16 | 10 | 1 | 34.71 | 15.57 | 2.230 | 15.44 | 2.248 | 12.37 | 2.807 |
| 16 | 10 | 16 | 42.22 | 27.26 | 1.549 | 26.85 | 1.573 | 22.06 | 1.914 |
| 16 | 10 | 64 | 138.03 | 92.62 | 1.490 | 91.04 | 1.516 | 80.79 | 1.708 |
| 16 | 10 | 256 | 547.45 | 341.66 | 1.602 | 336.36 | 1.628 | 282.94 | 1.935 |

</details>

<details>
<summary>NVIDIA H100 SXM 80GB (HBM3), SM90 (`sm_90a`, 132 SMs), CUDA 13.4: runtime token count (T 10 and 12), a state snapshot per token, 12 shapes, median kernel time (us)</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16 R5 (us) | speedup | FP16 RNE (us) | speedup |
|---|---|---|---|---|---|---|---|---|---|
| 10 | 80 | 16 | 336.38 | 192.79 | 1.745 | 192.91 | 1.744 | 130.35 | 2.581 |
| 10 | 80 | 64 | 970.51 | 695.94 | 1.395 | 637.61 | 1.522 | 446.19 | 2.175 |
| 10 | 80 | 256 | 3407.19 | 2686.80 | 1.268 | 2456.40 | 1.387 | 1748.60 | 1.949 |
| 10 | 20 | 16 | 104.21 | 61.14 | 1.704 | 59.81 | 1.742 | 39.28 | 2.653 |
| 10 | 20 | 64 | 334.59 | 192.79 | 1.736 | 192.92 | 1.734 | 129.78 | 2.578 |
| 10 | 20 | 256 | 968.19 | 695.26 | 1.393 | 636.34 | 1.521 | 445.68 | 2.172 |
| 12 | 80 | 16 | 393.42 | 228.70 | 1.720 | 229.18 | 1.717 | 153.32 | 2.566 |
| 12 | 80 | 64 | 1138.36 | 828.37 | 1.374 | 757.93 | 1.502 | 525.32 | 2.167 |
| 12 | 80 | 256 | 4007.45 | 3210.99 | 1.248 | 2947.89 | 1.359 | 2062.59 | 1.943 |
| 12 | 20 | 16 | 118.43 | 71.86 | 1.648 | 70.65 | 1.676 | 45.98 | 2.575 |
| 12 | 20 | 64 | 392.04 | 228.84 | 1.713 | 228.54 | 1.715 | 152.73 | 2.567 |
| 12 | 20 | 256 | 1133.28 | 828.92 | 1.367 | 757.26 | 1.497 | 525.94 | 2.155 |

</details>

### [03b1e4a](https://github.com/flashinfer-ai/flashinfer/commit/03b1e4a32855b7678a1981b23aa3e041efc6a8a2)

- **作者**: Adrian
- **时间**: 2026-11-26T01:43:13Z
- **提交信息**: test(mla): guard automatic wide splits by device plan (#10010)

<!-- .github/pull_request_template.md -->

## 📌 Description

The automatic wide-split determinism case in `test_cake_mla_splitkv.py`
fails on GB200 with:

```text
assert ([32, 32, ...] and 32 > 32)
```

`plan_kv_split` intentionally enables more than 32 splits only for the
listed device configurations: `(sm_100a, 148 SMs)` and `(sm_103a, 152
SMs)`, subject to the query-count and KV-length thresholds. Unlisted
configurations correctly keep the 32-split cap. The test fixture expands
the split-KV dispatch range to include the current device, but it does
not enable the planner's wide-split rule for that device. The
`rows1_kv131072` case nevertheless assumed that automatic planning
always selected more than 32 splits.

Before running the automatic case, compute its planned split count and
skip it when the device selects the narrow path. This matches the guard
already used by the adjacent wide-plan accuracy test. Explicitly forced
wide-split cases still run, and the automatic case retains coverage on
devices whose planner actually selects wide splits. The production
planner and kernels are unchanged.

## 🔍 Related Issues

Found while validating the image update in #9334 (following #9990).

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

- A temporary CPU harness using the actual planner and test control flow
reproduces the assertion before the fix. After the fix, an unlisted
SM100 configuration skips the automatic case, while the listed
SM100/SM103 configurations retain 64-split coverage.
- `FLASHINFER_WORKSPACE_BASE=/tmp/flashinfer-cu134-fix-workspace
PYTHONPATH=. python -m pytest --confcutdir=tests/mla
tests/mla/test_cake_mla_splitkv.py -k 'plan_wide_rule or plan or
binding_caps' -q`: **2 passed, 3 skipped, 156 deselected**.
GPU-dependent cases were skipped because this workspace has no working
GPU driver.
- Changed-file pre-commit hooks and `git diff --check` passed.

GPU determinism and CUDA graph replay validation remain pending. No new
test files were added.

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/mla/test_cake_mla_splitkv.py`

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

This PR addresses the MLA split-count assertion. The MiniMax
pre-attention numerical mismatches observed in the same CI pipeline are
a separate issue.

AI assistance: prepared and reviewed with Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* The wide-split determinism test now skips the automatically planned
131,072-token case when the device plans 32 or fewer splits. Forced
split-count cases are unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Brian K. Ryu <43616432+bkryu@users.noreply.github.com>

### [1a4b60f](https://github.com/flashinfer-ai/flashinfer/commit/1a4b60f75cf1f5bed21e272f1a3c5e8390f577e0)

- **作者**: milesial
- **时间**: 2026-11-26T00:46:12Z
- **提交信息**: perf(moe): cheaper ClampedRelu2 epilogue in the CuTe-DSL MoE GEMM1 (#8838)

<!-- .github/pull_request_template.md -->

## 📌 Description

The ClampedRelu2 epilogue of the SM100 CuTe-DSL MoE gather GEMM1
computes `relu(L * tanh(x / L)) ** 2`. Before this PR, it computed
`tanh` as `2 * sigmoid(2x) - 1` (ex2, add, rcp and two FMAs per element)
and multiplied by `L` and `1 / L` for every element. This PR makes the
epilogue cheaper in two ways:

- `tanh` uses `cute.math.tanh(fastmath=True)`, which lowers to one
`tanh.approx.f32`. Its max relative error (about 2^-11) is below the
rounding step of the FP4 and FP8 GEMM1 outputs.
- When the GEMM1 output is block-scaled (NVFP4 or MXFP8), the kernel
computes `relu(tanh(alpha / L * x)) ** 2` and folds `L ** 2` into the
output scale: the NVFP4 global factor, or the MXFP8 element scale. This
removes the per-element multiplies by `L`. Outputs without scale factors
keep the old form, with the faster `tanh`.

The kernel change is in
`blockscaled_contiguous_gather_grouped_gemm_act_fusion.py`.
`tests/moe/test_cute_dsl_mxfp8_moe.py` gets two new tests.

**Performance.** Setup: GB200, NVFP4 weights and activations,
ClampedRelu2 with `L = 7`, 128 experts, top-8, `swap_ab=False`,
autotuned. Each value is the median of 3 interleaved runs of 200 calls,
from 1 to 8192 tokens. Kernel times come from the PyTorch profiler, so
host launch gaps are not included.

Hidden 4096, intermediate 2048 (times in µs):

| Tokens | GEMM1 before | GEMM1 after | Speedup | MoE kernels before |
MoE kernels after | Speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 15.7 | 13.6 | 1.16x | 32.7 | 30.6 | 1.07x |
| 16 | 73.8 | 68.8 | 1.07x | 148.0 | 142.5 | 1.04x |
| 64 | 110.6 | 104.5 | 1.06x | 219.7 | 212.4 | 1.03x |
| 256 | 114.9 | 110.9 | 1.04x | 230.0 | 224.1 | 1.03x |
| 1024 | 124.3 | 113.1 | 1.10x | 247.1 | 235.1 | 1.05x |
| 2048 | 151.2 | 134.8 | 1.12x | 319.6 | 305.4 | 1.05x |
| 4096 | 256.8 | 233.4 | 1.10x | 549.6 | 517.2 | 1.06x |
| 8192 | 452.9 | 439.3 | 1.03x | 916.5 | 924.0 | 0.99x |

Hidden 2048, intermediate 768 (times in µs):

| Tokens | GEMM1 before | GEMM1 after | Speedup | MoE kernels before |
MoE kernels after | Speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 12.3 | 10.4 | 1.18x | 24.9 | 22.9 | 1.08x |
| 16 | 27.3 | 22.8 | 1.20x | 54.6 | 50.0 | 1.09x |
| 64 | 36.7 | 29.8 | 1.23x | 71.9 | 65.2 | 1.10x |
| 256 | 37.5 | 32.3 | 1.16x | 77.9 | 72.4 | 1.08x |
| 1024 | 39.4 | 32.9 | 1.20x | 86.0 | 77.8 | 1.11x |
| 2048 | 50.2 | 39.2 | 1.28x | 117.7 | 105.1 | 1.12x |
| 4096 | 90.1 | 63.2 | 1.42x | 205.0 | 168.2 | 1.22x |
| 8192 | 128.8 | 97.0 | 1.33x | 311.1 | 282.1 | 1.10x |

"MoE kernels" is the sum of all GPU kernel times in one
`cute_dsl_fused_moe` call. At 8192 tokens with hidden 4096, the MoE
total varies by about 5% between runs (881 to 952 µs), so the 0.99x is
within noise. GEMM1 is faster at every point.

<details><summary>Benchmark script</summary>

```python
"""GEMM1 and end-to-end time of the CuTe-DSL NVFP4 MoE with ClampedRelu2 (non-swap-AB path).

Run from the repository root: python bench_clamped_relu2.py [--tokens 1 16 ...]
"""

import argparse
import statistics

import torch

from flashinfer import cute_dsl_fused_moe
from flashinfer.autotuner import autotune
from flashinfer.tllm_enums import ActivationType
from tests.moe.utils import create_moe_tensors

p = argparse.ArgumentParser()
p.add_argument("--tokens", type=int, nargs="+", default=[1, 16, 64, 256, 1024, 4096])
p.add_argument("--hidden", type=int, default=4096)
p.add_argument("--inter", type=int, default=2048)
p.add_argument("--experts", type=int, default=128)
p.add_argument("--topk", type=int, default=8)
p.add_argument("--iters", type=int, default=200)
args = p.parse_args()

limit = torch.tensor([7.0], dtype=torch.float32, device="cuda")
print("tokens,gemm1_us,moe_kernels_us")
for t in args.tokens:
    tn = create_moe_tensors(
        num_tokens=t,
        hidden_size=args.hidden,
        intermediate_size=args.inter,
        num_experts=args.experts,
        num_local_experts=args.experts,
        top_k=args.topk,
        gated=False,
    )
    kw = dict(
        x=tn["x"],
        x_sf=tn["x_sf"],
        token_selected_experts=tn["token_selected_experts"],
        token_final_scales=tn["token_final_scales"],
        w1_weight=tn["w1_weight"],
        w1_weight_sf=tn["w1_weight_sf"],
        w1_alpha=tn["w1_alpha"],
        fc2_input_scale=tn["fc2_input_scale"],
        w2_weight=tn["w2_weight"],
        w2_weight_sf=tn["w2_weight_sf"],
        w2_alpha=tn["w2_alpha"],
        num_experts=args.experts,
        top_k=args.topk,
        activation_type=ActivationType.ClampedRelu2,
        clamped_relu2_limit=limit,
        swap_ab=False,
    )
    with autotune(True):
        cute_dsl_fused_moe(**kw)
    fn = lambda: cute_dsl_fused_moe(**kw)  # noqa: E731
    for _ in range(20):
        fn()
    torch.cuda.synchronize()
    # Kernel times from the profiler: GEMM1 median, and summed GPU kernel time per
    # MoE call (excludes host launch gaps).
    g1_times, total = [], 0.0
    with torch.profiler.profile(activities=[torch.profiler.ProfilerActivity.CUDA]) as prof:
        for _ in range(args.iters):
            fn()
        torch.cuda.synchronize()
    for e in prof.events():
        if e.device_type == torch.autograd.DeviceType.CUDA:
            total += e.device_time
            if "Gather" in e.name:
                g1_times.append(e.device_time)
    g1 = statistics.median(g1_times) if g1_times else float("nan")
    print(f"{t},{g1:.2f},{total / args.iters:.2f}", flush=True)
```

Run from the repository root, for example `python bench_clamped_relu2.py
--hidden 2048 --inter 768`.
</details>

## 🔍 Related Issues

Follow-up to #7286 (ClampedRelu2 in the CuTe-DSL fused MoE).

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/moe/test_cute_dsl_fused_moe.py
tests/moe/test_cute_dsl_mxfp8_moe.py`

On GB200: `tests/moe/test_cute_dsl_fused_moe.py` and
`tests/moe/test_cute_dsl_mxfp8_moe.py`, 841 passed and 22 skipped. The
existing ClampedRelu2 tests cover the folded path:

- NVFP4 (`w4a4`): accuracy check against the FP32 reference.
- MXFP8: both `swap_ab` settings, and a limit changed at runtime.

The new `test_mxfp8_clamped_relu2_huge_limit_is_relu2` checks that a
limit of `1e20` gives finite outputs that match plain ReLU^2.

At 66321c8b7 on B200 (SM100): the full
`tests/moe/test_cute_dsl_mxfp8_moe.py` (23 passed) and the 34
ClampedRelu2 cases of `tests/moe/test_cute_dsl_fused_moe.py` (34
passed). The same selection also passes at 80e9fc185 (22 and 34 passed).

After the rebase onto main 6a26a3bc7, at 715e0e597 on B200:
`tests/moe/test_cute_dsl_mxfp8_moe.py` (25 passed), the 34 ClampedRelu2
cases of `tests/moe/test_cute_dsl_fused_moe.py` (34 passed),
`tests/moe/test_routed_nvfp4.py` (153 passed) and
`tests/trace/test_cute_dsl_pre_fc2_reference.py` (34 passed).

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #

## Reviewer Notes

- **Numerics.** The output changes slightly, by at most about one
FP8/FP4 rounding step, because `tanh.approx.f32` replaces the sigmoid
form. The fold caps `L` at `2 ** 32`, so `L ** 2` stays finite in FP32.
For `|x| <= 2 ** 26`, the cap changes `L * tanh(x / L)` by less than the
`tanh.approx.f32` error. Without the cap, a limit above about 1.8e19
turned every output into NaN.
- **`epilogue_op`.** The fold applies only with the default identity
`epilogue_op`. A custom `epilogue_op` takes the unfolded path, so it
sees the full activation, not the activation divided by `L ** 2`. No
caller in the repository passes one.
- **`pre_fc2_routing`.** The fold is off with `pre_fc2_routing` (added
on main in #9260). That path quantizes with its own per-expert scale to
match its reference bit for bit, so it keeps the unfolded form.
- **Swap-AB.** The swap-AB kernel keeps the sigmoid form. Moving it to
`tanh.approx.f32` needs a matching change in
`tests/moe/test_helpers/cute_dsl_moe_swap_ab_reference.py`, so it is
left for a separate PR.
- AI-assisted (Claude Code). I reviewed every changed line and can
explain each choice.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* MXFP8 output with clamped ReLU² and SFC generation remains finite with
very large clamp limits.
* Small FC1 blocks produce finite results across ordinary and very large
clamp limits.
* Quantized output continues to match expected results when large clamp
limits are used.
* **Tests**
* Added checks comparing MXFP8 results with quantized reference outputs
for large clamp limits and small FC1 blocks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Alexandre Milesi <milesial@users.noreply.github.com>

### [51557e8](https://github.com/flashinfer-ai/flashinfer/commit/51557e8e0af6de60b5f1d8d73eebdad1c04f811b)

- **作者**: Vivian Chen NV
- **时间**: 2026-11-26T00:44:04Z
- **提交信息**: perf(prim_ts) keep D512 grouped Keeps for decode planned at a long max_kv_len (#9998)

## 📌 Description

#9771 selects grouped Keeps Q64 for D512 GQA8 decode with NVFP4 KV at
q_len > 1. That selection doesn't hold at every batch size and plan
length. When the Keeps grid doesn't fill a wave,
`_resolve_grouped_q_launch_candidates` limits Keeps to one wave of
splits (`multi_wave and (fills_wave or sm107_smem_transform)`). Swaps
Q64 can use up to 8 waves. Wherever the extra splits lower its modeled
time, Swaps Q64 wins.

This happens at some batch sizes with short plans: for example B13 with
32 Q / 4 KV heads at `max_kv_len` 8192 or 32768 picks `Sq64g8/s5`. It
happens at most batch sizes up to 32 once the plan is long. Engines such
as vLLM plan decode once at startup with `max_kv_len` set to the model
context (e.g. 262144) and capture the plan in CUDA graphs, so they hit
the Swaps path.

For D512, Keeps Q64 and Swaps Q64 score the same extra waves. This PR
lets D512 Keeps keep its multi-wave split fanout (`or probe.headdim ==
512`). The change set is exactly `Sq64g8/sN` → `Kq64g8/sN` with the same
split count N; nothing else changes.

**Performance** (B200, clocks unlocked, D512, 32 Q / 4 KV heads, FP8 Q,
NVFP4 KV, q_len 8 causal, plan `max_kv_len` 262144; µs, median over 6
processes, CUPTI timing):

| B | KV length | main | this PR | ratio |
|---|---|---|---|---|
| 8 | 1024 | 43.1 | 32.5 | 0.75 |
| 8 | 4096 | 62.9 | 47.2 | 0.75 |
| 8 | 16384 | 115.2 | 96.1 | 0.83 |
| 8 | 32768 (30720 shared prefix) | 174.2 | 135.9 | 0.78 |
| 8 | 131072 | 550.6 | 488.8 | 0.89 |
| 8 | 262144 | 1049.3 | 965.9 | 0.92 |
| 8 | half 8192, half 131072 | 383.6 | 312.3 | 0.81 |
| 32 | 16384 | 393.2 | 320.1 | 0.81 |
| 32 | 32768 | 634.4 | 549.6 | 0.87 |
| 32 | 262144 | 4749.1 | 4362.1 | 0.92 |

Short plans, same setup (each side is its tree's default selection; main
`Sq64g8/sN`, this PR `Kq64g8/sN` with the same N):

| B | q_len | plan `max_kv_len` | KV length | main | this PR | ratio |
|---|---|---|---|---|---|---|
| 13 | 8 | 8192 | 8192 | 107.2 | 89.1 | 0.83 |
| 13 | 8 | 8192 | 2048 | 62.2 | 48.4 | 0.78 |
| 13 | 8 | 32768 | 32768 | 281.5 | 235.6 | 0.84 |
| 13 | 8 | 32768 | 4096 | 81.0 | 63.8 | 0.79 |
| 13 | 8 | 32768 | alternating 2048 / 32768 | 180.9 | 143.7 | 0.79 |
| 24 | 8 | 2048 | 2048 | 67.8 | 52.8 | 0.78 |
| 30 | 8 | 32768 | 32768 | 578.6 | 506.4 | 0.88 |
| 6 | 32 | 8192 | 8192 | 139.5 | 105.8 | 0.76 |

- **Long plans.** Across 348 + 24 + 40 + 18 timed points, the PR is
0.71–0.93x of main wherever the config changes, and never slower. These
cover TP1/TP2 head splits, B 4–128, q_len 2–32 causal and dense, plans
40960–262144, and actual lengths 1K–256K. Points where main already
selects Keeps keep the same config.
- **Short plans.** Across 35 timed points where the config changes, the
PR is 0.75–0.88x of main, and every PR process was faster than every
main process. These cover heads 32/4, 16/2 and 8/1; B 5–115; q_len 2–32
causal and dense; plans 2048–32768; uniform and mixed actual lengths.
- **Why not one-wave Keeps.** Forcing one-wave Keeps instead is faster
than Swaps for uniform long batches. For mixed-length batches it is up
to 1.41x slower than main, which is why the multi-wave split fanout is
kept.
- **Correctness.** Every output was compared with an fp32 reference on
the E4M3-rounded K/V. Min cosine 0.99982.

**Scope** (plan-only, mocked 148-SM SM100, FP8 Q, NVFP4 KV, every B from
1 to 256, heads 32/4, 16/2 and 8/1, q_len 1–32, causal and dense):

| plan `max_kv_len` | plans | changed |
|---|---|---|
| 2048–32768 | 294,912 | 14,160 (q_len 2–32, B 5–126) |
| 40960–262144 | 245,760 | 20,532 (q_len 2–32, B 2–131) |
| 2048–32768, page 16 and 128 | 46,080 | 2,720 |

- Every changed config is `Sq64g8/sN` → `Kq64g8/sN` with the same N. No
Swaps Q64 config is left with this PR, and there were no errors on
either tree.
- No change for q_len 1. FP8 KV and GQA16 or 64/4 heads don't change at
any B (204,800 plans).
- At the changed long-plan timing points, the full plan config equals
main's with Keeps forced.


## 🔍 Related Issues

Follow-up to #9771.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran `pre-commit run --files` on the two
changed files; all hooks pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_decode.py`

`test_attention_ts_decode_d512_q8_auto_selects_grouped_keeps` now also
runs at `max_kv_len` 262144 (B8/16/32) and at B13 with `max_kv_len`
8192. For NVFP4 at those points it also asserts the split count. On main
it fails for NVFP4 at B13/8192 and B8/16/32/262144. With this PR, all 15
D512 selection cases pass, and the full
`tests/attention/test_attention_ts_decode.py` passes on B200 (640
passed).

## Reviewer Notes

The one-line change is in `_resolve_grouped_q_launch_candidates`. Keeps
stays one-wave-only for other head dims; I only measured D512.

---------

Signed-off-by: Vivian Chen <140748220+xuanzic@users.noreply.github.com>

### [6022b5e](https://github.com/flashinfer-ai/flashinfer/commit/6022b5e826714d92cf699a48d3b52f749fcf8063)

- **作者**: Alberto Massidda
- **时间**: 2026-11-26T00:42:24Z
- **提交信息**: feat(pcie_ipc): optional bounded wait for peers (FLASHINFER_PCIE_IPC_TIMEOUT_S) (#9112)

## Summary

Partially addresses #9108: bounds the all-reduce wait only. All-gather /
reduce-scatter will follow on top of this PR, building on #9436.

Every wait on a peer in the PCIe IPC all-reduce spins until the peer
arrives. A peer that never does (crashed, OOM-killed, or a rank that
took a different dispatch) leaves the other ranks spinning forever,
inside a CUDA graph where the host cannot see or interrupt it.

This PR adds an opt-in bounded wait:

- **Opt-in:** set `FLASHINFER_PCIE_IPC_TIMEOUT_S`. Each of the 27
peer-polling loops (barrier generations, `+0.0` sentinels, the CE ring
flag) then reads `%globaltimer` every 4096 polls.
- **On timeout:** past the deadline, one thread reports where it was
waiting and calls `__trap()`. The step fails with a CUDA error instead
of hanging.
- **Default unchanged:** unset or `0` compiles the guard out. The
default module (also the AOT one) produces a cubin byte-identical to
`main`.
- **Separate module:** a non-zero timeout builds a separate JIT module
(`pcie_ipc_comm_spin_timeout_<ns>`), the way the debug knobs in
`gen_pcie_ipc_comm_debug_module` already do.

## Changes

- `include/flashinfer/comm/pcie_ipc_all_reduce.cuh`: `SpinGuard`
(compiled out when `FLASHINFER_PCIE_IPC_SPIN_TIMEOUT_NS == 0`); the 26
polling loops become `for (SpinGuard spin; <cond>;
spin.tick(__func__))`.
- `include/flashinfer/comm/pcie_ipc_ce_ring.cuh`: the same for its flag
wait.
- `flashinfer/jit/comm.py`:
`gen_pcie_ipc_comm_module(spin_timeout_ns=0)`.
- `flashinfer/comm/pcie_ipc_ar.py`: reads
`FLASHINFER_PCIE_IPC_TIMEOUT_S`. It does not change the protocol, so
ranks with different values still interoperate.
- `tests/comm/test_pcie_ipc_spin_timeout.py`: env parsing, module naming
and flags, and a 2-GPU test where one rank skips a call and the other
must fail within the deadline instead of hanging.

Not touched: `pcie_ipc_ce_sm120.cuh` looks generated, so I left it
alone. The all-gather and reduce-scatter modules are also unchanged;
happy to extend the guard to them in a follow-up if this approach is
accepted.

## Test

- **CPU:** `pytest tests/comm/test_pcie_ipc_spin_timeout.py -k "not
missing_peer"` → 3 passed.
- **GPU, 2x RTX PRO 6000 Blackwell Server (sm_120, PCIe P2P), exclusive
node:**
- `pytest tests/comm/test_pcie_ipc_spin_timeout.py` → 4 passed,
including the missing-peer test;
- `FLASHINFER_PCIE_IPC_TIMEOUT_S=60 pytest
tests/comm/test_pcie_ipc_all_reduce.py` → 8 passed, 24 skipped (4 and 8
GPU cases), i.e. the guarded kernels give the same results.
- **Build:** for `FLASHINFER_CUDA_ARCH_LIST=12.0`, the default
`pcie_ipc_comm` cubin has the same sha256 as `main` (493,080 bytes). The
timeout build has the same 41 kernels plus the guard (696,040 bytes; the
report string is present).
- **GPU, 8x RTX PRO 6000 Blackwell Server, exclusive node** (4+4 GPUs
over two sockets), timeout build (`FLASHINFER_PCIE_IPC_TIMEOUT_S=60`):
  - `pytest tests/comm/test_pcie_ipc_spin_timeout.py` → 4 passed;
- `pytest tests/comm/test_pcie_ipc_all_reduce.py` → 32 passed, 0
skipped, covering the TP2, TP4 and TP8 cases including the island
kernels.
- `pre-commit` passes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optional timeout for PCIe IPC AllReduce peer waits. Set
`FLASHINFER_PCIE_IPC_TIMEOUT_S` to a nonzero number of seconds to make
an expired wait report an error instead of hanging. The default remains
unbounded.
* **Documentation**
* Clarified that an expired wait can leave the CUDA context unusable and
require a process restart. The timeout does not apply to the first-call
process-group collective when no launch configuration is specified, and
it does not detect ranks combining unrelated inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Alberto Massidda <amassidda@nvidia.com>
Co-authored-by: Alberto Massidda <amassidda@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f140884](https://github.com/flashinfer-ai/flashinfer/commit/f140884a14da101419e53d4198d18851e9661c97)

- **作者**: Vincent
- **时间**: 2026-11-26T00:40:04Z
- **提交信息**: feat(batch_invariant): LSE output and attention sinks for the batch-invariant attention class (#9683)

## 📌 Description

This PR adds two members to the batch-invariant attention class of #8590
(`batch_invariant=True` on `BatchDecodeWithPagedKVCacheWrapper`,
`BatchPrefillWithPagedKVCacheWrapper`,
`BatchPrefillWithRaggedKVCacheWrapper`): the LSE output and attention
sinks. Both were refused until now.

**Why.** A training forward needs the per-row LSE next to the output:
FlashAttention-style backward kernels recompute `P = exp(S - lse)` from
`out`, `lse`, `q`, `k`, `v`. With the LSE in the class, the rollout
kernels can be the training forward, with the same LSE bits in both.
Sinks are the one feature gpt-oss (head dim 64, a 128-token window,
per-head sinks) needs beyond what the class already had.

**LSE.** A second output of a row's final online-softmax state `(m, l)`:
`lse2 = m * c + lg2(l)` in base 2 (FlashInfer's convention, `c =
fp32(sm_scale * log2 e)`), and `lse2 * fp32(ln 2)` in base e, computed
in the kernel as a declared multiply. `lg2` is the pinned
`lg2.approx.ftz` the sampling class already uses. Requesting the LSE
never changes an output bit.

**Sinks.** `sinks` is an fp32 `[num_qo_heads]` tensor; head `h`'s rows
get one virtual key of logit `sinks[h]` and zero value, as on the other
backends (`sm_scale` is not applied to the sink; the LSE includes it).
In the class it is one merge step per row after the last chunk merge and
before the normalisation, in base-2 units, independent of tiling, unit
kind, kernel body, and prefill or decode. A `-inf` sink reproduces the
bits of the row without sinks.

**Identity.** The three class fingerprints (`attn-bf16-d64/128/256-...`)
and every output bit of a call without sinks are unchanged, with or
without the LSE. The new members have their own receipts:
`fingerprint(<wrapper>, head_dim=, causal=, lse_base=)` and
`fingerprint(<wrapper>, head_dim=, causal=, sinks=True[, lse_base=])`.
The LSE is a run-time mode of the existing kernels; sinks are
compile-time kernel variants (`..._sink`), so a call without sinks runs
kernels that contain no sink code.

**Both mask modes.** Both members are available in the causal class and
in the non-causal class of #9285 (prefill `causal=False`, multi-token
decode `is_causal=False`): they read a row's final `(m, l)`. Under the
non-causal class a row's LSE depends on its request's key count, its
head and its own query alone, and the sink joins that key set. The
non-causal members have separately named receipts,
`attn-bf16-d<D>-nc-lse-<base>-...`, `attn-bf16-d<D>-nc-sink-...` and
`attn-bf16-d<D>-nc-sink-lse-<base>-...` (kernels `..._nc_sink`); the
causal receipts are unchanged.

**API.**
- LSE as the non-invariant wrappers: `run(..., return_lse=True)` /
`run_return_lse` return `(out, lse)`, `lse` fp32 `(total_q,
num_qo_heads)`; an `lse=` buffer is validated and written in place. The
prefill wrappers take `lse_base` (`"log2"` default, `"ln"`) and
`lse_layout` (`"NH"`, `"HN"`); decode returns base 2.
- Sinks: `run(..., sinks=)` on the paged wrappers and the `_sinks`
attribute on the ragged one; read in place at every launch, so a
CUDA-graph replay sees updated values.
- `plan(..., has_sinks=None)`: an optional declaration. `True` makes a
`run()` without sinks raise and `False` a `run()` with sinks, so an
integrator that forgets sinks on one path gets an error instead of two
different members.
- Anything else (dtype, shape, device, buffers that overlap storage the
kernels read or write) raises `BatchInvariantUnsupportedError`.

**Performance** (B300, same-GPU A/B, ratios of speeds, geomean per head
dim). Without sinks and without the LSE, relative to main after this
merge: prefill 0.99x, decode 0.99x to 1.01x. LSE on relative to off:
0.99x to 1.00x. Sinks on relative to off: prefill 0.99x to 1.00x, decode
1.00x. With sinks at the gpt-oss shape, relative to the fastest
FlashInfer backend that serves sinks for the call: decode 0.98x to 1.16x
for batches of 8 to 256; paged prefill 0.82x (one 1K request), 0.97x
(one 8K request), 1.19x (8 x 2K), 1.25x (32 x 1K).

**Not included / follow-ups.** The backward itself; rows with no visible
key (needed, with a declared merge, for a context-parallel decode); a
window under the non-causal class (refused, as on main); natural-log LSE
on the decode wrapper; custom masks.

## 🔍 Related Issues

Follows #8590, #9301 and #9285; tracked in #9009.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed:
`tests/attention/test_batch_invariant_attention.py` (bitwise, in both
mask modes: LSE and sink bits equal across paged prefill, ragged
prefill, decode, multi-token decode and chunked prefill; batch /
permutation / sub-batch invariance; agreement over every kernel site;
output bits unchanged without sinks; accuracy against fp32 references;
the gpt-oss shape; a forty-request non-causal batch against
single-request runs; a device-free check that the mask mode reaches
every plan and kernel lookup; receipts pinned next to the unchanged
class fingerprints; refusals) and `tests/batch_invariant/test_lean.py`
(the Lean model of both members over the mode).
- [x] All tests are passing at this head: the attention suite (329
tests) gives 329 passed on SM107 (Rubin), 327 passed and 2 skipped on
SM103 (B300 and GB300) and 325 passed and 4 skipped on SM100 (GB200);
the skips are placement tests of main for parts with more shared memory
or the hardware row maximum. The regular wrappers' LSE and sink tests
pass on B300. The Lean build, conformance and axiom checks pass.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Brian K. Ryu <43616432+bkryu@users.noreply.github.com>

### [9ab9588](https://github.com/flashinfer-ai/flashinfer/commit/9ab958880daf64cfd28cecae42f019277d46c255)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-26T00:33:32Z
- **提交信息**: feat(batch_invariant): batch-invariant fp4 MoE backend for the unified `MoELayer` (NVFP4 x NVFP4 and MXFP4 x MXFP4; SM100 / SM103 / SM107) (#9901)

<!-- .github/pull_request_template.md -->

## 📌 Description

The third MoE PR of the batch-invariant series, following #9283 and
#9406. `BatchInvariantFp4Config()` is a backend candidate of the unified
MoE layer for the 4-bit-weight pairs, grouped as `TrtllmFp4Config`
groups them (`backend_key = "batch_invariant_fp4"`;
`QuantConfig(weight=..., activation=...)` selects the pair), named
explicitly through `BackendOptions` and never a default candidate. Two
pairs:
* **NVFP4 x NVFP4** -- the W4A4 classes `moe.nvfp4.<act>`.
* **MXFP4 x MXFP4** -- the classes `moe.mxfp4.<act>`.

```python
from flashinfer.fused_moe import (BackendOptions, BatchInvariantFp4Config, ExpertConfig, MoEActivationPack, MoEConfig, MoELayer,
                                  MoEWeightPack, QuantConfig, QuantFormat, RoutingConfig, SwiGLU)
from flashinfer.fused_moe.api import RoutingInputMode, RoutingMethodType

quant = QuantConfig(weight=QuantFormat.NVFP4, activation=QuantFormat.NVFP4)      # or weight=MXFP4, activation=MXFP4
cfg = MoEConfig(routing=RoutingConfig(num_experts=E, top_k=k, method=RoutingMethodType.Renormalize), quant=quant,
                experts=ExpertConfig(intermediate_size=I), activation=SwiGLU(), backend=BackendOptions((BatchInvariantFp4Config(),)))
layer = MoELayer(cfg)
weights = MoEWeightPack()
weights.prepare_for("batch_invariant_fp4", BatchInvariantFp4Config.prepare_weights(
    w1, w2, quant=quant, num_local_experts=E, hidden_size=H, intermediate_size=I, activation=SwiGLU()))   # bf16 experts, quantized here
out = layer(MoEActivationPack(x, None, routing_input_mode=RoutingInputMode.FromLogits, routing_logits=logits), weights)   # bf16 x
```

One runner (`BatchInvariantFp4Runner`,
`fused_moe/batch_invariant/runner_fp4.py`) and one op
(`api_fp4.fused_moe_fp4`) serve both pairs through an `Fp4Pair`
descriptor (the scale block, the instruction classes, the quantizer,
whether the pair carries the per-tensor alphas and the per-token scale);
the weight view is tagged with its pair and a pack prepared for the
other pair is refused. A pair the backend does not serve is skipped by
the layer's candidate filter and refused by `prepare_weights` /
`prepare_activations` / `check_support` with
`BatchInvariantUnsupportedError` naming the served pairs (MXFP4 x MXFP8
among them: the next PR of the stack). The kernel classes keep their
registry names (`moe.nvfp4.<act>`, `moe.mxfp4.<act>`;
`fingerprint("fused_moe_nvfp4" | "fused_moe_mxfp4", ...)`; one JIT
module `batch_invariant_moe` with the fp8 and bf16 bodies).

Both pairs take the three routing input modes of the bf16 backend (from
logits through the shared route kernels: `Default`, `Renormalize`,
`RenormalizeNaive`, `Sigmoid`, `SigmoidRenorm`, `TopK`, `TopKSigmoid`,
`Llama4` top-1 and `DeepSeekV3` with or without its expert groups;
pre-routed ids and weights under any `RoutingConfig`), every typed
activation of the layer (gated on the (gate, up) pair: `SwiGLU` with any
`alpha` / `beta` / `limit`, `SwiGLUStep`, `GeGLU`, `GeGLUTanh`, `SiTU`,
`PowLU`; ungated: `ReLU2`, `Identity`, `GELU`, `ReLU`, `SiLU`), bf16
activations (quantized inside the op) or a pre-quantized pack, bf16
expert weights quantized at preparation, on SM100 / SM103 / SM107.
Refused with the mode's error and no fallback: `do_finalize=False` (the
slot-order combine is part of the class), expert-parallel shards
(`local_expert_offset` / `local_num_experts`: the class's EP form is not
part of this backend), fused shared experts.

**What is promised.** (R1) two runs give the same bits; (R2) a token's
bits do not change with the batch (alone, in another batch, permuted, in
any sub-batch, with any load on its experts); (R3) every record of the
grouped block-scaled space and of the swapped decode space, every
persistent-grid size and every SM count gives the same bits, so the
layer's autotuner may pick any of them; (R4) the packings of the
expanded rows, the routing input modes and the pre-quantized pack forms
agree on their inputs. The dataflow is stated in Lean and the CPU model
is bit-exact on the part; the classes are checked against that model
only, with the dense `mm_fp4` class (NVFP4 and MX) as the GEMM oracle.
Nothing is promised relative to FlashInfer's other fp4 backends (their
quantizers and chains are other specifications).

**Contract.** Weights: `prepare_weights` takes the canonical bf16 `w1
[E, 2I, H]` (rows `[up, gate]`) or `[E, I, H]` for the ungated
activations and `w2 [E, H, I]` and quantizes every expert with the
pair's quantizer class (NVFP4: the per-tensor global scale `448 * 6 /
amax` per expert and GEMM, the alphas `1 / global_scale` stored; MXFP4:
the UE8M0 block scales, no global scale); the per-expert global scales,
computed or caller-supplied, are validated with the mode's error before
any expert is quantized (finite, positive and normal); `intermediate` /
`intermediate_scales` select the NVFP4 static class and are refused for
MXFP4. `H` and `I` multiples of 32, the expert weight shapes unsplit by
the dense class's chunk rule, `1 <= top_k <= min(E, 16)`, `E <= 1024`;
the output bf16 `[T, H]`; `T = 0` returns the empty output (a
pre-quantized pack with either scale shape too). Activation packs
(`MoEActivationPack`; anything else raises, nothing falls back):

| pair | `hidden_states_q` | `hidden_states_scale` | `per_token_scale` |
|---|---|---|---|
| both | bf16 `[T, H]` | `None` | `None` (the class quantizes the rows
itself) |
| NVFP4 | uint8 `[T, H / 2]` (e2m1 pairs) | the 128x4 swizzled buffer of
`nvfp4_quantize(..., layout_128x4)` (uint8 or e4m3; as returned or
flattened) or the linear `[T, H / 16]` layout; where the two shapes
coincide (`T` a multiple of 128, `H` of 64)
`QuantConfig(swizzled_scale_factors=True / False)` names the layout, and
a tensor named linear must have the linear shape; the 128x4 buffer's pad
columns (`H` not a multiple of 64) are zero, as every FlashInfer
quantizer writes them | `[T]` f32 with
`QuantConfig(per_token_scale=True)` (the layer's shared pack contract);
absent: unit scales (the per-tensor pack of
`TrtllmFp4Config.prepare_activations` enters the same chain) |
| MXFP4 | uint8 `[T, H / 2]` | the 128x4 buffer of `mxfp4_quantize(...,
layout_128x4)` (uint8 or e8m0; as returned or flattened) or the linear
`[T, H / 32]` layout; the same naming rule where the shapes coincide
(`T` a multiple of 128, `H` of 128); zero pad columns (`H` not a
multiple of 128) | none: the flag and a pack scale are refused |

A pre-quantized pack is a different quantization of `x` than the bf16
path's (the per-tensor pack at unit per-token scales for NVFP4, or the
caller's quantizer), so its bits equal the class composed on its own
bytes, not the bf16 path's; the tests pin both. The weight view names
its pair (`quant`) and its intermediate class (`intermediate`): a view
without either key is declined by the layer's candidate filter and
refused by the runner driven directly. A cached autotune winner whose
GEMM1 record is the gather form, replayed on a pack whose scale layout
cannot feed that form, takes the record's box form (a placement: the
same bits).

**Shared code.** The branch edits the shared MoE blocks
(`blocks/kernel.py`, `epilogue.py`, `swap.py`, `compile.py`,
`permute.py`, `pdl.py`, `mterm.py`) and the dense block-scaled GEMM
blocks (`gemm/batch_invariant/*`) to add the block-scaled operand and
chain blocks. The bf16 and fp8 kernels are unchanged: one grouped and
one swapped object per class compile at this head to the same names and
byte-identical objects (SHA-256) as #9406's, and the bf16, fp8 and
pack-contract suites pass at this head on sm_107 and at the previous
head on sm_100 (the reviewer's run). One shared behaviour changes:
`fingerprint("fused_moe_bf16" | "fused_moe_fp8" | ..., method=Llama4,
top_k > 1)` is refused, as the runners refuse that routing term (it
returned a receipt for a class no layer builds).

**Attribution.** The kernels of this backend took optimisation ideas
from the package's other MoE backends, each adopted as a placement of
the class's dataflow (the same bits, placed as those kernels place
theirs): the swapped-AB decode records as ranked members of the
dispatcher's space follow Prims-TS (its swap-AB low-latency templates
and tile-N ladder) and TRTLLM-Gen's fp4 decode tactics; the
static-intermediate class follows the fp4-intermediate recipe of the
CuTe-DSL, TRTLLM-Gen, CUTLASS and Frost backends (every op correctly
rounded); the dense packing of the expanded rows with the scale factors
at the padded atom positions and the token tile's scale rows gathered by
one `cp.async` warp follow CuTe-DSL's gathered-operand pipeline; the PDL
wait / trigger placement and the launch's tile bound on the persistent
grid follow Prims-TS and TRTLLM-Gen; the routing, permutation, combine
and the ranking contract are the bf16 backend's; the bodies, the operand
/ epilogue block interfaces and the review-round rules are the fp8
per-tensor backend's.

### Performance

Compare against every eligible FlashInfer backend of the pair through
`MoELayer` on the same weights, inputs and routing. GPUs: Rubin NVL4
(sm_107, 212 SMs) and B200 (sm_100); method: cold-L2 CUDA-graph replay,
batched events (CUPTI at decode), the median of three interleaved
rounds; the batch-invariant class's bits are asserted at every point.
Ratio = fastest existing backend of the cell / the batch-invariant class
(> 1: the batch-invariant class is faster), geomean over the regime's
cells (Qwen3-30B, Qwen3-235B, Mixtral 8x7B, DeepSeek-V3, Nemotron3-30B
shapes; the cell count per regime in the long form). Rubin (sm_107) with
this head's arithmetic; the B200 (sm_100) columns from the same protocol
on an earlier head.

**NVFP4 x NVFP4 (per-token class)** vs the fastest existing backend of
each cell (TRTLLM-Gen, CuTe-DSL, Prims-TS, CUTLASS, cuDNN Frost); each
cell "from logits / pre-routed". The B200 autotuned and from-logits
columns are the exact-arithmetic class's rows (the SFU chains were not
re-timed there); by the Rubin and the B200 pre-routed ratios this head's
class is 0-15 % faster than those entries at mid and prefill, equal at
decode:

| regime | Rubin untuned | Rubin autotuned | B200 untuned | B200
autotuned |
|---|---|---|---|---|
| decode (T <= 16) | 0.73 / 0.84 | 0.73 / 0.85 | 0.77 / 0.86 | 0.76 /
0.80 |
| mid (64 <= T <= 1024) | 1.06 / 0.84 | 0.86 / 0.83 | 0.84 / 0.82 | 0.76
/ 0.76 |
| prefill (T >= 4096) | 1.39 / 0.83 | 1.04 / 0.69 | 0.89 / 0.86 | 0.69 /
0.63 |
| all | 0.99 / 0.84 | 0.85 / 0.80 | 0.83 / 0.84 | 0.74 / 0.74 |

**MXFP4 x MXFP4**: no existing MXFP4 x MXFP4 MoE kernel runs on these
parts, so the reference is the fastest MXFP4 x MXFP8 (W4A8) kernel of
the cell, a different pair with half the activation bits; the B200
column is the exact-arithmetic class's rows (this head's class is 0-7 %
faster per the Rubin ratios):

| regime | Rubin untuned | Rubin autotuned | B200 untuned |
|---|---|---|---|
| decode (T <= 16) | 0.75 / 0.92 | 0.73 / 0.91 | 0.77 / 0.87 |
| mid (64 <= T <= 1024) | 1.11 / 1.03 | 0.94 / 0.97 | 0.99 / 0.95 |
| prefill (T >= 4096) | 1.52 / 1.31 | 1.34 / 1.24 | 1.22 / 1.15 |
| all | 1.04 / 1.05 | 0.93 / 1.01 | 0.95 / 0.96 |

Against the correctly rounded exponential and divisions, the SFU chains
are within one per cent at decode and up to 12 % (NVFP4) / 7 % (MXFP4)
faster at prefill on Rubin, more on the B200, where GEMM1's epilogue
chain is the bound; the outputs differ in a few elements per ten
thousand through the intermediate quantization's code flips.

## 🔍 Related Issues

<!-- Link any related issues here -->

#9009

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
* Added batch-invariant MoE support for NVFP4×NVFP4 and MXFP4×MXFP4 on
supported GPUs, with routing and supported activation options.
  * Added optional static intermediate quantization for NVFP4.
* Added dense and padded layouts, plus swapped and gather execution
paths.
  * Exposed the FP4 backend configuration through the public API.
* **Documentation**
* Documented supported FP4 configurations, activation behavior, and
conformance coverage.
* **Tests**
* Added coverage for FP4 outputs, routing, layouts, deterministic
execution, and conformance.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [cd47e0d](https://github.com/flashinfer-ai/flashinfer/commit/cd47e0d34e7598aac8c51e59ceee22f76b8d9de5)

- **作者**: ranx2026
- **时间**: 2026-11-26T00:12:24Z
- **提交信息**: fix(ci): write Git alternates with a line feed (#9543)

## 📌 Description

`tests/test_sharding/test_merged_source.py` fails 2 of 4 cases on native
Windows arm64.

- `scripts/pr_checks/merged_source.py` writes
`.git/objects/info/alternates` with `Path.write_text`, which translates
the trailing line feed to the platform line ending.
- On Windows the file ends with CRLF.
- Git reads the carriage return as part of the object directory path:
`object directory ...\.git\objects? does not exist`.
- Every object lookup of the pinned merge then fails, and the helper
raises `ValueError: Could not prepare pinned merged source`.
- The second failing case expects two explicit fetches, `[base, head]`,
through a path remote; on Windows it sees `[base]` only.
- `git fetch --filter=blob:none <path>` registers the path remote as a
promisor remote.
- Linux Git refuses a promisor remote whose name begins with `/`, so the
head is fetched explicitly there and the expectation holds.
- Windows Git accepts the drive-letter path and fetches the head lazily
during `cat-file -e`, so the explicit head fetch never runs.

This change:

- writes the alternates file with `newline="\n"`, so Git reads the same
bytes on every platform;
- lets the test accept the fetch list `[base]` or `[base, head]`; the
tree check that follows keeps proving both commits arrived from the
remote.

The second case is a test expectation, not a product defect: the
production helper fetches from the named remote `origin`, a promisor
remote.

## 🔍 Related Issues

Related: #8431 (native Windows arm64 build support).

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
reviewers may adjust): `tests/test_sharding/test_merged_source.py`

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

- Verified on a Windows 11 arm64 workstation with a Blackwell GPU, on
main at `9b69c0e` plus the build support of #8431.
- With this change: 4 passed in about 11 s.
- Without this change on the same kind of workstation: 2 failed, 2
passed, with the two errors above.
- Those runs were on main at `119cf05` and `646988d`, each plus the
build support of #8431.
- WSL2 and Linux pass all 4 cases without this change.
- Their behavior is unchanged: `newline="\n"` writes the line feed they
wrote already, and their fetch list `[base, head]` still passes the
relaxed assertion.
- The `newline` parameter of `Path.write_text` exists on every Python
version this project supports.
- `pre-commit` (ruff) leaves both files unchanged.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed an issue that could alter object-store paths on platforms with
different newline handling.
* **Tests**
* Updated shallow-clone checks to allow Git to fetch the head during the
base fetch while still verifying fetch order.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4862
- **最后更新**: 2026-11-26T09:27:23Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34983
- **最后更新**: 2026-11-27T01:46:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 430
- **最后更新**: 2026-11-25T20:48:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13444
- **最后更新**: 2026-11-27T00:42:39Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

## DiffSynth-Studio 昨日提交分析（第 1/1 批，共 2 条）

### 1. 主要更新类型
- **功能新增**：Diffutoon-2 —— 基于 MiniMax-H3 的双 ControlNet 动漫/卡通风格化功能（PR #1860）
- **Bug 修复**：修复非 NVIDIA GPU 上的 dtype 问题（PR #1861）
- **附带更新**：文档（中英文）、README、示例代码与预处理工具同步更新

### 2. 关键变更点及与项目方向的关系
- **Multi-ControlNet 组合框架**：为 MiniMax-H3 支持多控制视频列表及各自缩放系数，是项目"多模态生成流水线"方向的自然扩展，将 ControlNet 能力从图像进一步推进到视频领域。
- **pin_latents / return_latents 机制**：提供跨窗口的潜在空间连续性控制，解决长视频分段生成中的接缝与漂移问题，体现项目对**长视频一致性**的持续投入。
- **Diffutoon-2 预处理工具链**：`video_lineart`、`video_blur`、`video_caption` 将线稿提取、模糊控制与字幕生成整合为标准流水线，降低用户使用门槛。
- **dtype 修复**：紧跟功能合入后立即修复非 NVIDIA GPU（如 AMD、Apple Silicon）的精度问题，表明项目重视跨平台可移植性。

### 3. 对项目的影响和潜在意义
- 为 DiffSynth-Studio 引入一条完整的**视频卡通化生产链路**（示例参数 σ=15、控制系数 0.4/0.4、max_pixels≈100 万像素已给出最佳实践），可直接用于动画制作、内容二创等场景。
- 双 ControlNet（线稿 + 颜色，9 层权重）提供更精细的风格控制维度，增强与同类视频生成工具的竞争力。
- 紧随功能合入的 dtype 修复说明 CI/多硬件测试覆盖在改善，降低非 CUDA 用户的安装与运行风险。

### 4. 值得关注的技术点
- **跨窗口潜在一致性**：`pin_latents` 的设计是长视频生成的核心难点，其接口形式（可选开关）值得关注后续是否被其他视频模型复用。
- **双模块 ControlNet 架构**：线稿与颜色分离的 9 层权重设计，兼顾风格还原与色彩可控，可作为多 ControlNet 融合的参考实现。
- **AI 辅助开发痕迹**：提交包含 Claude Opus 协作署名，反映项目已将 AI 代码协作纳入工作流，值得观察其对迭代速度与代码质量的长期影响。
- **非 NVIDIA GPU 的 dtype 处理**：涉及跨设备精度管理，对 PyTorch 生态下的多硬件兼容有借鉴意义。

### 5. 基于项目背景的发展影响
DiffSynth-Studio 定位为多功能扩散合成工作室，覆盖图像、视频等多种生成任务。本次提交：
- **拓展了视频生成的能力边界**，将 Diffutoon 系列从既有版本升级到 Diffutoon-2，巩固项目在"可控视频风格化"细分领域的积累；
- **强化了工程成熟度**，功能与 Bug 修复在同一天内连续落地，体现活跃的社区协作与快速响应能力；
- **完善了用户生态**，通过示例脚本、中英文文档和预处理工具降低上手成本，有助于吸引更多研究者与创作者基于该平台构建应用，进一步巩固其作为 ModelScope 生态中重要生成工具的地位。

综上，这组提交在一天内完成了"新功能落地 + 跨平台修复 + 文档配套"的完整闭环，既扩展了项目的技术版图，也提升了对非主流硬件用户的友好度。

## 详细提交记录

### [c6c916e](https://github.com/modelscope/DiffSynth-Studio/commit/c6c916e42429bc278f952c93966a48e75db87e10)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-26T12:02:26Z
- **提交信息**: Bugfix: dtype (#1861)

* Add Diffutoon-2: dual ControlNet toon stylization on MiniMax-H3

Framework (minimal):
- Multi-ControlNet composition for MiniMax-H3 (list of control videos/scales)
- Optional pin_latents / return_latents for clean latent continuity across windows

Diffutoon-2:
- Weights DiffSynth-Studio/Diffutoon-2 (line-art + color modules, 9 layers)
- Preprocess utils: video_lineart, video_blur, video_caption
- Example MiniMax-H3-Diffutoon.py (σ=15, scales 0.4/0.4, max_pixels=1,032,192)
- Docs en/zh

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

* caption_revise

* refine code

* refine code

* update docs

* update readme

* update docs

* fix dtype issues on non-nvidia gpus

---------

Co-authored-by: Yuze <StevenSun@sjtu.edu.cn>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [100a41c](https://github.com/modelscope/DiffSynth-Studio/commit/100a41c7904e11eb3e0f7c2cd2c5e20d2d2180e7)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-26T09:23:05Z
- **提交信息**: Support Diffutoon-2 (#1860)

* Add Diffutoon-2: dual ControlNet toon stylization on MiniMax-H3

Framework (minimal):
- Multi-ControlNet composition for MiniMax-H3 (list of control videos/scales)
- Optional pin_latents / return_latents for clean latent continuity across windows

Diffutoon-2:
- Weights DiffSynth-Studio/Diffutoon-2 (line-art + color modules, 9 layers)
- Preprocess utils: video_lineart, video_blur, video_caption
- Example MiniMax-H3-Diffutoon.py (σ=15, scales 0.4/0.4, max_pixels=1,032,192)
- Docs en/zh

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

* caption_revise

* refine code

* refine code

* update docs

* update readme

* update docs

---------

Co-authored-by: Yuze <StevenSun@sjtu.edu.cn>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 39108
- **最后更新**: 2026-11-27T02:22:00Z

## 提交统计

- **昨日提交总数**: 83
- **提交者数量**: 55
- **主要提交者**: Chunan Zeng, William Hu, Stanislav Petrov

## AI分析总结

# SGLang 昨日提交综合分析（共 83 条）

## 一、主要更新类型分布
- **Bug 修复**约 26 条，占近半数，覆盖调度器、KV 缓存管理、NPU/AMD 后端、diffusion、CUDA Graph 上限等模块。
- **功能新增**约 22 条，集中在新模型（MAGI-2、Qwen4-Exp、Inkling-2-Mini、GigaChat 4、kimi-k3、MiniMax-H3、deepseek-v4.1/v4-pro）、新硬件能力（NPU Ascend A3 W8A8 + DSpark、MLU 的 GQA/MLA）与 PD 分离架构。
- **性能优化**约 16 条，涉及 DFlash 单次 launch、DSA 稀疏 MLA kernel 预编译、CUDA Graph、量化 kernel、kimi-k3 SP 集合通信、UMT5 编码器加载、rust-server 阻塞池解码等。
- **文档/CI/重构**约 19 条，含 cookbook 部署指南（GB300、NPU）、多硬件 CI 对齐、接口抽象重构与 Rust tree 核心重构。

## 二、关键变更与项目方向
- **多模态/Diffusion 成为主战场**：近三分之一提交与 diffusion 相关——MAGI-2、Wan2.2 语音转视频、prompt 重写、租户隐私隔离、LoRA/精度优化、Breakable CUDA Graph（突破 CUDA Graph 不可中断限制，利好变步长去噪）、diffusion GT 对齐 CANN 版本建立多硬件数值一致性标准。SGLang 正从纯 LLM 推理扩展为统一的多模态生成服务平台。
- **硬件多元化深化**：NPU（昇腾 DSA KV INT8、MegaMoE 融合算子、eplb、A3 W8A8）、MLU（GQA/MLA 补齐、流水线维护）、AMD（aiter 修复）、Intel XPU CI、NVIDIA（DSV4/MXFP8、NVFP4 KV 跨 TP 传输）并行推进，多后端战略从"NVIDIA 优先"走向全硬件覆盖。
- **PD 分离架构完善**：单 token 请求直接在 prefill 应答、MoriTransport 抽象、busy 计数修复、MiniMax 稀疏状态按 layer 配对、NVFP4 page-row KV 跨 attention TP 归一化传输，直接服务大集群 disaggregated serving。
- **推理核心持续打磨**：投机解码（DFlash、MTP）与稀疏注意力（Prims-TS 稀疏 MLA 编译时机、qsa indexer）成为核心性能战场；KV 缓存管理（row_width 统一、SWA 窗口修复）、xgrammar 升级巩固基础。

## 三、对项目的影响与潜在意义
- 大量内存管理与调度器修复（req_to_token row_width、tokenizer SHM 释放）提升长时运行稳定性，降低内存泄漏与崩溃风险。
- 租户隐私隔离与请求取消机制表明项目正面向**生产级多租户部署**演进，与 README"高效服务"定位一致。
- 新硬件/新模型开箱即用体验提升，尤其国产芯片部署门槛显著降低；高频模型接入显示生态合作活跃。
- 稀疏 kernel 预编译与单 launch 优化减少首 token 延迟，利好高吞吐服务；CI 稳定性投入（replay expiry、cuda graph 比较、runner 配置）保障快速迭代下回归可控。
- 短期风险在于多硬件、多模型导致测试矩阵膨胀，CI 基础设施对齐提交正对应这一挑战。

## 四、值得关注的技术点
- **Rust 化趋势**：rust-server 支持多模态取消、将大请求体解码移入阻塞池避免阻塞异步运行时，性能与安全并重。
- **AI 辅助开发深度融入**：多条提交 Co-authored-by 为 Claude Opus 5.5 / Fable 5.1 / Mythos 5.2 等，反映开发流程变革。
- **量化 KV 工程难点突破**：NVFP4 低精度 KV 在 PD 分离下的跨 TP 归一化传输。
- **多硬件数值一致性验证**：Diffusion GT 对齐 CANN 版本的做法值得借鉴。

## 五、整体判断
这些提交共同推动 SGLang 向"统一的 LLM + 多模态生成推理引擎"演进：一方面通过大量修复提升核心服务的生产就绪度，另一方面以 diffusion 和多硬件支持拓宽能力边界。性能优化占比近三成且集中在投机解码、稀疏注意力、集合通信等推理关键路径，与项目"极致速度"的核心叙事高度一致；文档与 cookbook 持续更新（GB300 部署、SemiAnalysis 合作）强化了商业化落地形象。整体看，项目处于功能扩张与工程质量并重的高速迭代期，正为下一阶段生态规模化和商业化部署奠定基础。

## 详细提交记录

### [a9a27e9](https://github.com/sgl-project/sglang/commit/a9a27e9255863d44e15a2965b9cf550ffcd19e9b)

- **作者**: chuyeh
- **时间**: 2026-11-26T21:10:03Z
- **提交信息**: [Fix] [AMD] aiter: Fix NEXTN draft extend crash on the CK kernel (#40872)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [d90fe9e](https://github.com/sgl-project/sglang/commit/d90fe9eddf6257d5f1e54945878650bd755f1263)

- **作者**: Mick
- **时间**: 2026-11-26T19:50:04Z
- **提交信息**: [Doc] diffusion: Align the add-diffusion-model skill's BCG output check with the performance guide (#53305)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [fa3e206](https://github.com/sgl-project/sglang/commit/fa3e20650e3f00ad2c4e0f0ac0de792894789de9)

- **作者**: Mick
- **时间**: 2026-11-26T19:49:06Z
- **提交信息**: [Doc] diffusion: Document offline Wan2.2 speech-to-video generation (#53429)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [56625e2](https://github.com/sgl-project/sglang/commit/56625e255ede1f968df898099c291d2a342d659f)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-11-26T19:48:21Z
- **提交信息**: [Fix] diffusion: keep TP/Ulysses head shards on the unsharded torch SDPA kernel (#43242)

### [0730305](https://github.com/sgl-project/sglang/commit/0730305dbee380a841640c50510ebe3e9e1d9302)

- **作者**: Mick
- **时间**: 2026-11-26T19:42:58Z
- **提交信息**: [Perf] [NVIDIA] diffusion: Read both TP ranks' partial sums in MiniMax-H3's gate kernels (#52480)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a74b2c1](https://github.com/sgl-project/sglang/commit/a74b2c17741db8bc8522ff6e720924ab043f35a9)

- **作者**: Mick
- **时间**: 2026-11-26T19:09:53Z
- **提交信息**: [Feat] diffusion/lingbot: Add optional prompt rewriting (#52528)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Pan Li <pandalee@ustc.edu>

### [07a17a3](https://github.com/sgl-project/sglang/commit/07a17a305cf017ccc7995d2bf23841ec9e219d44)

- **作者**: Mick
- **时间**: 2026-11-26T18:29:16Z
- **提交信息**: [Fix] diffusion/serving: Protect request privacy and scope media jobs to tenants (#51786)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [43584fa](https://github.com/sgl-project/sglang/commit/43584fa4170e74679e390b6473a5de2d46662abc)

- **作者**: Pan Li
- **时间**: 2026-11-26T17:43:57Z
- **提交信息**: [Feat] diffusion/model: Support MAGI-2-preview (#35014)

Signed-off-by: Pan Li <pandalee@ustc.edu>
Co-authored-by: niehen6174 <1639206518@qq.com>

### [7867032](https://github.com/sgl-project/sglang/commit/786703226704d58d5df8bbe64bd1f5a160d0f263)

- **作者**: Mick
- **时间**: 2026-11-26T17:37:22Z
- **提交信息**: [Perf] diffusion/wan: Load the UMT5 text encoder in BF16 by default (#52655)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [981a334](https://github.com/sgl-project/sglang/commit/981a3340fbc640236d0ef03567adf1e1aa9d18f4)

- **作者**: Shuwen Wang
- **时间**: 2026-11-26T16:02:45Z
- **提交信息**: [Refactor] unified_cache: Drop the unreachable legacy linker config fallback (#53128)

### [0de0689](https://github.com/sgl-project/sglang/commit/0de06898bdb266e8164d3cf84bf8e3c71092cc93)

- **作者**: Khoa Pham
- **时间**: 2026-11-26T15:10:12Z
- **提交信息**: [Fix] kimi-k3: Allow the fake PD transfer backend under K3.1 DCP (#53392)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [e49df2e](https://github.com/sgl-project/sglang/commit/e49df2e59890c0f5a5ce2c19416a9a404c0343ca)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-26T14:36:16Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main 90afb027 (#53390)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c59dfc0](https://github.com/sgl-project/sglang/commit/c59dfc02ccf01d2543036a7747cf3b4f6d305baa)

- **作者**: Yixin Dong
- **时间**: 2026-11-26T14:20:34Z
- **提交信息**: [Feat] xgrammar: Support Lark grammars and bump to 0.2.9 (#39380)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [b921535](https://github.com/sgl-project/sglang/commit/b921535dc728a5e2d9aa13ba48122cb52b3a64e1)

- **作者**: Khoa Pham
- **时间**: 2026-11-26T14:04:20Z
- **提交信息**: [CI] speculative: Set _use_triton_accept_bonus on the DFlash ragged verify test worker (#53340)

### [95d8632](https://github.com/sgl-project/sglang/commit/95d86324f7f448d0b014de1fbd2ef722bb6bf71f)

- **作者**: Tarrun Pitta
- **时间**: 2026-11-26T13:54:07Z
- **提交信息**: [Fix] parser: Accept reasoning_content and empty join in response templates (#49885)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [7c34003](https://github.com/sgl-project/sglang/commit/7c340037b242bf18aeace60d473d1f0c7a3f2c2e)

- **作者**: weireweire
- **时间**: 2026-11-26T13:13:32Z
- **提交信息**: [Perf] [NVIDIA] dsv41: Lift 1024-row decode limits in fused mHC post and FlashInfer MXFP8 autotune (#53032)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [5e5e0d7](https://github.com/sgl-project/sglang/commit/5e5e0d79049c898ab6ed4e18ec0f91f25c08c56f)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-26T13:01:13Z
- **提交信息**: [Perf] diffusion/hy-nomas: Capture single-event offline denoising with breakable CUDA graphs (#52918)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [a6be22b](https://github.com/sgl-project/sglang/commit/a6be22b60e0800b2ea2aa471616fda5af02f52d3)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-26T13:00:03Z
- **提交信息**: [Perf] diffusion/cosmos3: Capture Bimanual denoise blocks with breakable CUDA graphs (#52657)

### [1233330](https://github.com/sgl-project/sglang/commit/12333306338da15038e910aa73103f3b42ee7b2e)

- **作者**: heziiop
- **时间**: 2026-11-26T12:35:54Z
- **提交信息**: [Fix] [NPU] dsa: Preserve global DSA top-k for MTP seed export (#51017)

### [d7fc792](https://github.com/sgl-project/sglang/commit/d7fc792a849da6f9137b73d3feaf41ee8e7c7d51)

- **作者**: Yuejia Tong
- **时间**: 2026-11-26T12:09:46Z
- **提交信息**: [Feat] [NPU] DSpark: Load the GLM-5.2 Speculators draft for static decoding on NPU (#38860)

### [dd87c5f](https://github.com/sgl-project/sglang/commit/dd87c5fd0b197649ae259c1aad5cfa517c06d274)

- **作者**: magicYang1573
- **时间**: 2026-11-26T11:54:37Z
- **提交信息**: [Feat] hicache: Add unified Engram store and support Qwen4-Exp (#46248)

Co-authored-by: root <root@lshb-reservedpool-xbwvd-1.int.xiaohongshu.com>
Co-authored-by: Teng Ma <stmatengss@gmail.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: Zhangheng <hzh0425@apache.org>

### [7295050](https://github.com/sgl-project/sglang/commit/7295050f4bced8e60f3e155fef117e76ff958a2d)

- **作者**: Артем Савкин
- **时间**: 2026-11-26T11:33:37Z
- **提交信息**: [Fix] [NPU] CI: Align workflows and diffusion GT with CANN 9.2.0 (#53106)

### [2217136](https://github.com/sgl-project/sglang/commit/221713687e005c7bf044f97d7ca8c98015c119b6)

- **作者**: Erik Wijmans
- **时间**: 2026-11-26T11:12:14Z
- **提交信息**: [Feat] pd: Answer a one-token request on the prefill server without a decode (#53153)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [8703754](https://github.com/sgl-project/sglang/commit/870375452ae12db9c3db0b1de5a38be2327a54f7)

- **作者**: Junlin Wu
- **时间**: 2026-11-26T10:18:28Z
- **提交信息**: [Fix] [NPU] profiler: :bug: Fix patches and daemon trace parsing (#47856)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [c6b72da](https://github.com/sgl-project/sglang/commit/c6b72da53d04cce3254e0b47302ac33638b2298d)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-26T10:15:04Z
- **提交信息**: [Refactor] attention: Derive each backend's KV table bounds once from the pool (#53314)

### [a987a5b](https://github.com/sgl-project/sglang/commit/a987a5b1947d63549bb50e1bb3d2778f477ab27c)

- **作者**: shun8686
- **时间**: 2026-11-26T09:41:49Z
- **提交信息**: [CI] [NPU] test: Require Mooncake for the DSV4-Flash 0731 W8A8 PD GPQA case (#53322)

### [e5efb8f](https://github.com/sgl-project/sglang/commit/e5efb8f30fabf11f79e7f2cf1a71dc2dbf8b3fd7)

- **作者**: metamergebot
- **时间**: 2026-11-26T09:31:29Z
- **提交信息**: [Fix] hicache: store the SWA window a storage query finds missing in buffer mode (#52956)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [2ef5a07](https://github.com/sgl-project/sglang/commit/2ef5a07b3f695fc6fde6843eddfd11a80c480d4b)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-26T09:31:14Z
- **提交信息**: [CI] inkling2: Run the vision attention unit test eagerly on aarch64 hosts (#53289)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [03c1c76](https://github.com/sgl-project/sglang/commit/03c1c76911582528057e0c4016525797a5337938)

- **作者**: metamergebot
- **时间**: 2026-11-26T09:20:44Z
- **提交信息**: [Fix] cuda-graph: Size the default decode graph ceiling to the per-rank running limit (#52709)

Co-authored-by: cctry <17473714+cctry@users.noreply.github.com>

### [92c86a5](https://github.com/sgl-project/sglang/commit/92c86a5569149703606c4674d9cd6a3b01c971e1)

- **作者**: metamergebot
- **时间**: 2026-11-26T09:19:58Z
- **提交信息**: [Fix] tokenizer: Release multimodal SHM on failed dispatch and transfer ownership at enqueue (#53064)

Co-authored-by: Shubham Garg <52582943+shub-garg@users.noreply.github.com>

### [8702b3b](https://github.com/sgl-project/sglang/commit/8702b3b3b82c772b790b38e0284e7b05c6738aca)

- **作者**: metamergebot
- **时间**: 2026-11-26T09:16:17Z
- **提交信息**: [Fix] scheduler: Count all non-idle time in the PD prefill busy counter (#53147)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [2396565](https://github.com/sgl-project/sglang/commit/23965658c955f2f1122c93d5351b131294258473)

- **作者**: metamergebot
- **时间**: 2026-11-26T09:15:40Z
- **提交信息**: [Feat] mem_cache: Build the Rust tree core from an empty index tensor instead of a device string (#53152)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: angelayi <angelayi@users.noreply.github.com>

### [f7d115f](https://github.com/sgl-project/sglang/commit/f7d115f4c27637bfc11c50ea4a65b4efd2a6dae6)

- **作者**: metamergebot
- **时间**: 2026-11-26T09:13:32Z
- **提交信息**: [Fix] scheduler: Retire sliding-window KV behind the window when a streaming session extends its own row (#52959)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: CoderHam <CoderHam@users.noreply.github.com>

### [c723acf](https://github.com/sgl-project/sglang/commit/c723acf775eccc7b9b5a298a1578ade83fe8c56a)

- **作者**: metamergebot
- **时间**: 2026-11-26T09:12:21Z
- **提交信息**: [Feat] rust-server: Cancel a request's multimodal processing when it is aborted (#52705)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [91fee1b](https://github.com/sgl-project/sglang/commit/91fee1bd8a373f773dd424ad20942241fb73d2b5)

- **作者**: chuyeh
- **时间**: 2026-11-26T09:03:28Z
- **提交信息**: [Fix] disaggregation: Use row_width in decode Mamba pool tests (#53296)

### [385262c](https://github.com/sgl-project/sglang/commit/385262cabbae1ce315ce0576e0219b4e56f29288)

- **作者**: qiye
- **时间**: 2026-11-26T08:24:53Z
- **提交信息**: [Feat] [NPU] dsa: Store the DSA MLA KV cache as INT8 on Ascend A2 (#49502)

Signed-off-by: Jianliang Qi <jianliang5669@gmail.com>
Co-authored-by: xiedeyantu <czjourney@163.com>

### [32129ac](https://github.com/sgl-project/sglang/commit/32129ac985f9c6f48f06060928eada7bc97a246e)

- **作者**: sglang-bot
- **时间**: 2026-11-26T07:59:12Z
- **提交信息**: [Doc] blogs: Sync LMSYS SGLang blog cards (#49415)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [dc0062a](https://github.com/sgl-project/sglang/commit/dc0062a455260953ff40588737ddfb6394844140)

- **作者**: Dante
- **时间**: 2026-11-26T07:59:02Z
- **提交信息**: [Fix] scheduler/pp: Bound dynamic chunk profiling by free KV capacity (#51481)

Co-authored-by: Dante <246460053+ccuuy@users.noreply.github.com>
Co-authored-by: Codex <codex@openai.com>

### [67db72e](https://github.com/sgl-project/sglang/commit/67db72ea4aabc64527b4152ef23ecb8d7d46a5c2)

- **作者**: Ma Mingfei
- **时间**: 2026-11-26T07:57:34Z
- **提交信息**: [Fix] test: Add missing moe runtime context to CPU graph fixture (#53259)

### [51f7e81](https://github.com/sgl-project/sglang/commit/51f7e81e85e27d5d800baeb601010148aa9cc1cb)

- **作者**: zilong
- **时间**: 2026-11-26T07:56:35Z
- **提交信息**: [Fix] encoder: Abort waiting requests before draining embeddings in the same tick (#51519)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [46516b9](https://github.com/sgl-project/sglang/commit/46516b938a7ed29ee0ae1f04ba80805549bcee5c)

- **作者**: Yuedong Wu
- **时间**: 2026-11-26T07:56:18Z
- **提交信息**: [Fix] scheduler: Emit scheduler status while idle (#51169)

Signed-off-by: Yuedong Wu <dwcn22@outlook.com>

### [b0f145c](https://github.com/sgl-project/sglang/commit/b0f145c8fedab08fcb140f2d2806850854507f70)

- **作者**: Ankur Singh
- **时间**: 2026-11-26T07:35:36Z
- **提交信息**: [Doc] cookbook: Pin the Qwen3.5 H200 AgentX lanes of InferenceX #5236 to its measured run (#53280)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3fb90c2](https://github.com/sgl-project/sglang/commit/3fb90c282d562c5bc3399bc05eb8afe666d7a60a)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-26T07:29:45Z
- **提交信息**: [Fix] diffusion/krea2: Prepare one latent row per requested output (#52119)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [b50b6db](https://github.com/sgl-project/sglang/commit/b50b6dbfd5fefd687356c2716c02fe2a34d887f5)

- **作者**: Ruilin Gao
- **时间**: 2026-11-26T07:29:03Z
- **提交信息**: [Perf] diffusion: Resolve the default output quality with the request's data type (#52601)

### [5fc4c77](https://github.com/sgl-project/sglang/commit/5fc4c77d0e41aff5143d97a2d676f3db36939010)

- **作者**: Ruilin Gao
- **时间**: 2026-11-26T07:28:48Z
- **提交信息**: [Perf] diffusion/lora: Compute fp32 dynamic adapters in the activations' dtype (#52064)

### [5c7aa3b](https://github.com/sgl-project/sglang/commit/5c7aa3b66e5ec7219e07edef91fdb8132c7c5dbe)

- **作者**: Kyungmin Lee
- **时间**: 2026-11-26T07:28:32Z
- **提交信息**: [Fix] moe: Honor swiglu_limit in FlashInfer TRT-LLM BF16 (#52257)

Signed-off-by: lkm2835 <lkm2835@gmail.com>

### [c6f02a0](https://github.com/sgl-project/sglang/commit/c6f02a003dc2234e9feccac696e2f876fbc7f0a9)

- **作者**: xiaoke12345678
- **时间**: 2026-11-26T07:28:17Z
- **提交信息**: [Fix] kernels/quantization: Use int64 row offsets in the per-token int8 quant kernel (#51196)

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [1d09c10](https://github.com/sgl-project/sglang/commit/1d09c106f19d2a6b33380f0adfd6e7d38bb7968a)

- **作者**: yingluobailu
- **时间**: 2026-11-26T07:28:02Z
- **提交信息**: [Fix] benchmark: Validate serving request rates before setup (#52077)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [38b4064](https://github.com/sgl-project/sglang/commit/38b406442cd016ddf7c1e7d3ae225cbdd9295a98)

- **作者**: Ruilin Gao
- **时间**: 2026-11-26T07:27:46Z
- **提交信息**: [Fix] diffusion: Load musubi-tuner Wan LoRAs (#51784)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [095e69c](https://github.com/sgl-project/sglang/commit/095e69cfd64a3822df37c8cdba3d5147e03e15cc)

- **作者**: 渺如星辰
- **时间**: 2026-11-26T07:27:31Z
- **提交信息**: [Fix] compressed-tensors: Treat actorder aliases like their canonical form in WNA16 MoE (#49804)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [26b1a51](https://github.com/sgl-project/sglang/commit/26b1a51814fce9d21e0aa05555b1b7168a5e3829)

- **作者**: zilong
- **时间**: 2026-11-26T07:27:17Z
- **提交信息**: [Fix] paged-experts: Cap auto K at the disk tier plan kernel limit (#51498)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Jan Schalkamp <schalkamp@bitside.de>

### [dbb0748](https://github.com/sgl-project/sglang/commit/dbb0748931ee0e8db154ff3fe0588af4e2fd69bd)

- **作者**: jacky.cheng
- **时间**: 2026-11-26T07:12:18Z
- **提交信息**: [Chore] [AMD] mono-kernel: Pin sgl-amd-mono at ba75a45 for the Qwen3.5 FP8 smallm_router and Triton 3.8 GEMV fixes (#52533)

### [fa0ac70](https://github.com/sgl-project/sglang/commit/fa0ac709b8cce57f9ea9b295dfbd6ab23e48d373)

- **作者**: ashwini rathi
- **时间**: 2026-11-26T07:08:57Z
- **提交信息**: [CI] [Intel] ci/xpu: Read-only tokens and no persisted git credentials in the Intel XPU nightly, release and monitor workflows (#53018)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a3b3867](https://github.com/sgl-project/sglang/commit/a3b3867b2642533331438c02a68988ded2ebc943)

- **作者**: AndyLi429
- **时间**: 2026-11-26T07:01:13Z
- **提交信息**: [Fix] [NPU] eplb: Support packed NZ expert dtype views (#51129)

Co-authored-by: AndyLi429 <AndyLi429@noreply.gitcode.com>

### [62891fa](https://github.com/sgl-project/sglang/commit/62891face2acda943737d78132d6fa1efa6ef6fa)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-26T06:56:34Z
- **提交信息**: [Refactor] mem_cache: Own the req_to_token row width on the pool as row_width (#53249)

### [f8130d0](https://github.com/sgl-project/sglang/commit/f8130d045d139c0ac1ccf08caa2032d59d5952fe)

- **作者**: chenxu214
- **时间**: 2026-11-26T06:39:00Z
- **提交信息**: [Feat] [NPU] moe: Add MegaMoE fused_op support for prefill and decode (#50691)

Co-authored-by: ShaqG <jingshanshi2001@gmail.com>

### [5121270](https://github.com/sgl-project/sglang/commit/512127045d08d161b99e71b7ea56ea165191cc61)

- **作者**: Wenbo Jiang
- **时间**: 2026-11-26T06:04:58Z
- **提交信息**: [Refactor] pd: Extract MoriTransport behind the common Transport interface (#47462)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6387cea](https://github.com/sgl-project/sglang/commit/6387ceafcc0ce2fa66fc5c4c6aebe46f1de90d22)

- **作者**: Rohit Nagraj
- **时间**: 2026-11-26T05:46:54Z
- **提交信息**: [Doc] cookbook: Add Qwen3.5 GB300 PP2 AgentX deployments / 补充 Qwen3.5 GB300 PP2 AgentX 部署 (#53253)

Signed-off-by: Rohit Pujar Nagraj <rpujarnagraj@nvidia.com>

### [eecd996](https://github.com/sgl-project/sglang/commit/eecd9969a98bf90a5154156116968e7f5d869dca)

- **作者**: Ruilin Gao
- **时间**: 2026-11-26T05:33:54Z
- **提交信息**: [Fix] diffusion/wan-ti2v: Build the first-frame mask per sample so n > 1 works (#51505)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [8fafc95](https://github.com/sgl-project/sglang/commit/8fafc95709c01a74955a6a13cb070f4c035ae989)

- **作者**: qiaonan02
- **时间**: 2026-11-26T05:31:10Z
- **提交信息**: [Fix] pd: Size decode Mamba spec-state scratch by running batch, not decode extra slots (#44015)

### [5ff04f1](https://github.com/sgl-project/sglang/commit/5ff04f14f46ac86072e8d2596faa8a734b6f1133)

- **作者**: garry569
- **时间**: 2026-11-26T05:20:44Z
- **提交信息**: [Fix] pd: Pair MiniMax sparse state by layer id under PP (#47610)

Co-authored-by: garry569 <324435785+garry569@users.noreply.github.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1b38828](https://github.com/sgl-project/sglang/commit/1b38828feaae401bf1efeca6bf920cb609b7d009)

- **作者**: Yuwei An
- **时间**: 2026-11-26T04:58:21Z
- **提交信息**: [Perf] speculative: Build the DFlash committed block in one launch (#52452)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [4817721](https://github.com/sgl-project/sglang/commit/48177212585eeaabca4db7e434c00a9c8a7ae604)

- **作者**: Chunan Zeng
- **时间**: 2026-11-26T04:45:24Z
- **提交信息**: [Feat] inkling2: Support Inkling-2-Mini (#51926)

Co-authored-by: Ke Bao <ispobaoke@gmail.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>
Co-authored-by: Kate Cheng <203210648+katec846@users.noreply.github.com>
Co-authored-by: Xiaoyu Zhang <35585791+BBuf@users.noreply.github.com>
Co-authored-by: Aurick Qiao <6137920+aurickq@users.noreply.github.com>
Co-authored-by: Long(Tony) Lian <longlian@berkeley.edu>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cc48b03](https://github.com/sgl-project/sglang/commit/cc48b03937aaa134f7cfe04ac583db342fe9de5c)

- **作者**: pllimax
- **时间**: 2026-11-26T04:41:10Z
- **提交信息**: [CI] [NPU] tests: CANN 9.2.0 nightly images, scheduled PR-run detection, 397b w4a8 env cleanup (#52431)

### [2d3a7e1](https://github.com/sgl-project/sglang/commit/2d3a7e161e6e6098bc2ae2b13a833c439794f02c)

- **作者**: Mick
- **时间**: 2026-11-26T04:35:29Z
- **提交信息**: [Test] Diffusion: Refresh Wan2.1 I2V LoRA H100 reference frames (#53157)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [b5f086d](https://github.com/sgl-project/sglang/commit/b5f086dcbd6684c5521b7515fb9f901a7ba438c6)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-26T04:26:06Z
- **提交信息**: [Fix] [AMD] docker: Bump TileLang to v0.1.12 for apache-tvm-ffi 0.1.11 (#53131)

### [aeb61a0](https://github.com/sgl-project/sglang/commit/aeb61a036f587ac3db1c05a690371d13b995be51)

- **作者**: chenxb002
- **时间**: 2026-11-26T04:08:45Z
- **提交信息**: [Feat] [MLU] attention: Add GQA and MLA support (#49214)

Co-authored-by: Yihao Wang <42559837+AgainstEntropy@users.noreply.github.com>

### [3fccbb3](https://github.com/sgl-project/sglang/commit/3fccbb3ca7c0742c5c3eb42e40202da80b8751e3)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-26T04:08:01Z
- **提交信息**: [Fix] qsa: Give the indexer test fake the index_n_heads that _forward_impl reads (#53238)

### [16ddadf](https://github.com/sgl-project/sglang/commit/16ddadf3119607aac39e735f0b53b919ec9fb0bb)

- **作者**: chenxb002
- **时间**: 2026-11-26T03:56:53Z
- **提交信息**: [CI] [MLU] workflows: Update runner group and labels (#53195)

### [08515d2](https://github.com/sgl-project/sglang/commit/08515d2bc96518a04d1a7e3921f306d8e6ee44a9)

- **作者**: Shuwen Wang
- **时间**: 2026-11-26T03:36:52Z
- **提交信息**: [Fix] tests: Stabilize replay expiry and cover GigaChat4 streaming (#53225)

### [71f7ad0](https://github.com/sgl-project/sglang/commit/71f7ad05316b7b99cbf6042807894e2bfed295c1)

- **作者**: ZY Y
- **时间**: 2026-11-26T03:12:04Z
- **提交信息**: [Test] [NPU] deepseek-v4-pro: Raise prefill mem-fraction-static to 0.85 (#53213)

### [7f00b8e](https://github.com/sgl-project/sglang/commit/7f00b8e55bac8f644e31e6de8d56c38bbba36d5a)

- **作者**: Stanislav Petrov
- **时间**: 2026-11-26T02:48:54Z
- **提交信息**: [Feat] gigachat4: Add GigaChat 4 support (#50613)

Co-authored-by: Alexey Samoylov <samojlovaleksej43452@gmail.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [d1c2712](https://github.com/sgl-project/sglang/commit/d1c2712fed799af211e61cf0fa52bd5ee70bd577)

- **作者**: Devashish Lal
- **时间**: 2026-11-26T02:38:43Z
- **提交信息**: [CI] permissions: set cooldown interval to 0 minutes for dlal-sgl (#53201)

### [a2f0638](https://github.com/sgl-project/sglang/commit/a2f06383bc78ec4a8b89955c313c1dcb7bf003da)

- **作者**: Colin-sun
- **时间**: 2026-11-26T02:37:34Z
- **提交信息**: [Doc] [NPU] cookbook: add Qwen3-Next NPU deployment (#38800)

### [d5101d1](https://github.com/sgl-project/sglang/commit/d5101d1719647c5d2585ed3454d6c7633b33d312)

- **作者**: Ke Bao
- **时间**: 2026-11-26T01:55:08Z
- **提交信息**: [Feat] pd: Transfer NVFP4 page-row KV between different attention TP sizes (#51234)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [fffff68](https://github.com/sgl-project/sglang/commit/fffff68d7d1e09fafee9ee47c188e325552dd0df)

- **作者**: Yuwei An
- **时间**: 2026-11-26T01:45:16Z
- **提交信息**: [Perf] dsa: Compile the Prims-TS sparse MLA kernels when the backend is built, not on first use (#52451)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [910492f](https://github.com/sgl-project/sglang/commit/910492fc8d0dbb250487212940abd5e66f5891da)

- **作者**: Khoa Pham
- **时间**: 2026-11-26T01:44:49Z
- **提交信息**: [Perf] kimi_k3: Enable the SP collective for 2-rank attention groups (#53196)

### [a662e1e](https://github.com/sgl-project/sglang/commit/a662e1efbb0f14549254b2ca492353c24d10392c)

- **作者**: HEX1A0A
- **时间**: 2026-11-26T01:34:13Z
- **提交信息**: [Feat] [NPU] deepseek-v4.1: Support Ascend A3 W8A8 inference and DSpark (#50205)

Co-authored-by: AndyLi429 <68410213+AndyLi429@users.noreply.github.com>
Co-authored-by: AndyLi429 <AndyLi429@noreply.gitcode.com>

### [fcddafc](https://github.com/sgl-project/sglang/commit/fcddafc1331b268a914fc0324bc18bfe9ef21f90)

- **作者**: Lee Nau
- **时间**: 2026-11-26T01:15:21Z
- **提交信息**: [CI] cuda_graph: Compare the prebuilt-state line with its own rank's capture line (#53160)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [42077e3](https://github.com/sgl-project/sglang/commit/42077e314c85cb59ca86954f4039ba324e79ecc3)

- **作者**: 黄孝君
- **时间**: 2026-11-26T00:55:43Z
- **提交信息**: [CI] [NPU] docker: Bump NPU kernel to 2026.11.0.post15 (#53102)

### [cfa0093](https://github.com/sgl-project/sglang/commit/cfa00939ab3056cb0913a0b34e8dc32ad2d4480d)

- **作者**: Mick
- **时间**: 2026-11-26T00:54:09Z
- **提交信息**: [Doc] skills: Rename the diffusion add-model skill to add-diffusion-model and align it with the new-model guide (#53174)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [9517e8b](https://github.com/sgl-project/sglang/commit/9517e8b70bc4dcd4d20e20c9fdcd0b10fc8702f7)

- **作者**: metamergebot
- **时间**: 2026-11-26T00:21:56Z
- **提交信息**: [Perf] rust-server: Decode large /generate bodies on the blocking pool (#53068)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [8430230](https://github.com/sgl-project/sglang/commit/84302308c2090620cf4dc422b90637f00a1828be)

- **作者**: William Hu
- **时间**: 2026-11-26T00:06:57Z
- **提交信息**: [Perf] [NVIDIA] kimi-k3: Run SP's side-stream reduce-scatter on 8 blocks (#53187)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1309
- **最后更新**: 2026-11-26T07:15:44Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 3
- **主要提交者**: Butterfingrz, DefTruth, ShimonMalnick

## AI分析总结

# `vipshop/cache-dit` 昨日提交分析

## 1. 主要更新类型

本次 9 笔提交覆盖**文档/技能沉淀**（4 笔）、**功能新增**（1 笔）、**性能优化**（2 笔）、**Bug 修复**（1 笔）与**构建重构**（1 笔），是一次以知识固化为主、核心能力演进为辅的均衡迭代。

## 2. 关键变更点与项目方向的关系

- **软缓存能力正式落地**：新增 Residual Motion 校准器（sigma-secant 残差外推）与可选的 SoftCache 模式（沿用 SeaCache 刷新规则 + headroom 采样跳步）。两者均**默认关闭、按需启用**，遵循项目一贯的"零侵入、可选增强"设计。
- **并行与通信性能持续深耕**：Ulysses 路径上对 FP8 打包存储做对齐 uint2 合并写、对 FP4 做同类优化，并将 FP4/FP6/FP8 通信默认收敛到 QKVO + per-group-16，直接服务 README 强调的"Parallelism + Quantization"主线。
- **分布式/注意力后端知识体系化**：新增 `cache-dit-distributed` 技能（ParallelismConfig、CP 计划 DSL、Ring/Ulysses/USP、TP 规划器、CP+TP 混合网格、TE/VAE/ControlNet 并行路径及"新增规划器"操作手册），并重命名注意力技能为 `cache-dit-attention`，统一在 `AGENTS.md` 注册——项目开始系统沉淀面向 AI 协作者的开发知识。
- **构建与兼容性收口**：NVCC 线程环境变量更名为 `CACHE_DIT_NVCC_THREADS`（csrc 合并为单一扩展后旧名失效），并适配 torch 2.15 的 collectives API。

## 3. 对项目的影响和潜在意义

- **功能层面**：SoftCache 与 Residual Motion 直接对标 arXiv 2610.22369，补齐了"缓存刷新策略"这一维度，使 DBCache 从"预测式缓存"进化为"可自适应跳步的缓存"，有望进一步压缩 DiT 推理步数。
- **性能层面**：存储合并与默认粒度收敛减少 Ulysses 通信的显存带宽占用与事件延迟；H3 批量本地 VAE tile 解码则优化了视频类管线的解码吞吐。
- **工程质量层面**：技能文档 + 操作手册的沉淀显著降低新贡献者（或 AI 代理）接入并行/注意力后端的门槛，是项目走向成熟协作模式的信号。

## 4. 值得关注的技术点

- **sigma 网格自适应**：Residual Motion 在 flow-matching 的 sigma（而非步数）上度量残差，天然适配非均匀调度器；SoftCache 重排 FlowMatch Euler 调度后被移除的步以 `dt=0` 填充，不产生计算开销。
- **torch.compile 兼容性**：SoftCache 的 `norm1` 探针在已编译 transformer 上可能不触发，项目通过一次性警告 + 全步计算兜底，并专门修复探针存活问题——这类"探针式缓存"与编译器的交互是隐蔽的坑。
- **被否决方案的记录价值**：提交中明确记录被拒绝的 FP6 存储、FP8 负载宽度变体及 128-bit shuffle 方案与验证结果，形成可复用的负空间知识。

## 5. 对项目发展的整体影响

结合 README 定位（Cache、Parallelism、Quantization、CPU Offload 一体的 PyTorch 原生 DiT 推进引擎），这批提交呈现出清晰的**双轮驱动**格局：一方面在"Cache"主线上引入业界最新的 SoftCache/Residual Motion 以保持算法前沿性；另一方面在"Parallelism + Quantization"主线上做底层通信与解码的微架构级优化以夯实性能底座。与此同时，大量技能文档的产出说明项目正从"功能堆叠"阶段过渡到"知识可复用、可协作"阶段，为后续更复杂的分布式能力（如 CP+TP 混合网格的规模化应用）打下组织与工程基础。整体上，这些提交在不破坏默认行为的前提下稳步推进，体现了较高的工程成熟度。

## 详细提交记录

### [d96a44c](https://github.com/vipshop/cache-dit/commit/d96a44c0549b46f97ac41657939d0fd8fc2fdb06)

- **作者**: DefTruth
- **时间**: 2026-11-26T11:28:03Z
- **提交信息**: docs(skill): add distributed skill and rename attention skill (#1423)

Add cache-dit-distributed covering ParallelismConfig/backend derivation, the CP plan DSL and split/gather hooks, Ring/Ulysses/USP plus the communication primitives (quantized and async Ulysses), TP planners and the CP+TP hybrid mesh, and the TE/VAE/ControlNet parallelism paths, with a per-model planner inventory and add-a-planner runbook. Rename cache-dit-attention-integration to cache-dit-attention and register both in docs/developer_guide/AGENTS.md.

Closes #1422

### [69da25f](https://github.com/vipshop/cache-dit/commit/69da25fe8d7bd6a335dea976560b6526c7d23e2a)

- **作者**: DefTruth
- **时间**: 2026-11-26T11:13:10Z
- **提交信息**: docs(skill): add attention backend integration skill (#1421)

Cover the dispatch chain, NHD/LSE/CP/mask contract, precedents (ffpa-attn, SageAttention-2/3, Sol-Attn, flash-varlen) and the acceptance matrix; register the skill in docs/developer_guide/AGENTS.md.

Closes #1420

### [dec1fde](https://github.com/vipshop/cache-dit/commit/dec1fde6c4feee4c66677072d8f517e3554274ba)

- **作者**: DefTruth
- **时间**: 2026-11-26T10:28:32Z
- **提交信息**: docs(skill): record SoftCache / Residual Motion verdict in cache integration skill (#1419)

Add the implemented SoftCache judgment (PR #1418) to the cache-integration skill: a verdict row in SKILL.md plus landscape.md sections 2.9 and 4.10 with the same-harness FLUX acceptance table, the scheduler-rewrite structural constraints and the torch.compile probe pitfall.

### [d75dfc3](https://github.com/vipshop/cache-dit/commit/d75dfc3c3b25b5cfa3c630ff099a432aef3a8085)

- **作者**: ShimonMalnick
- **时间**: 2026-11-26T10:00:13Z
- **提交信息**: feat(softcache): Residual Motion calibrator + opt-in SoftCache mode for DBCache (#1418)

* feat: add Residual Motion calibrator (sigma-secant residual extrapolation) for DBCache

Residual Motion is the predictor of SoftCache (arXiv 2610.22369). It moves the cached residual along the
secant of the last two real anchors, measured in the flow-matching sigma rather than the step count, so
it stays right on non-uniform sigma grids. With one anchor it reuses that residual.

The sigma comes from the scheduler at the step index SeaCache uses: the pipeline's scheduler, or
`residual_motion_scheduler` passed to `enable_cache` for transformer-only caching. Nothing is bound
unless this calibrator is selected, so every other path is unchanged.

Selectable via `ResidualMotionCalibratorConfig`, `enable_residual_motion` in YAML and
`--calibrator residual_motion` on the CLI.

* feat: add opt-in SoftCache (official SeaCache refresh rule + headroom sampler jumps) for DBCache

SoftCache (arXiv 2610.22369) refreshes with SeaCache's own rule: it accumulates the step-to-step
relative L1 change of the SEA-filtered, modulated input of the first block, and computes the step in
full once the sum reaches `softcache_tau`. On a cached step it enlarges the sampler step by a factor
that grows with the unspent budget and re-spaces the rest of the FlowMatch Euler schedule in place;
removed steps become dt=0 padding that runs no compute.

Opt-in via `DBCacheConfig(enable_softcache=True, softcache_tau=...)` on top of `enable_seacache=True`;
any existing calibrator predicts the cached steps. Residual Motion then reads each step's sigma from
the re-spaced schedule. If the first block's `norm1` probe never fires (e.g. `enable_cache` on an
already-compiled transformer) it warns once and computes every step. Default behaviour is unchanged.

* docs: SoftCache user guide, CLI flags, example YAML and load test

* style: docformatter

* fix(softcache): keep the probe alive under torch.compile and harden the guards

- wrap `norm1.forward` behind `torch.compiler.disable` instead of a forward hook:
  compiled code calls a submodule's `forward` directly, so the hook fired only
  while tracing and `--compile --cache --softcache` silently computed every step
- read the Residual Motion sigma at the scheduler's own step index, so a true-CFG
  pipeline neither skips schedule slots nor re-anchors two steps on one sigma
- measure a sampler step once when the pipeline calls the transformer twice
- return padded steps before the offload hook, so `--cpu-offload` moves no weights
- only unwrap our own probe on disable, leaving later `forward` wrappers intact
- reject steps_computation_mask, multi-transformer, out-of-range
  tau/jf_max/sigma_hi/raw_rel_l1_max, and a `residual_motion_scheduler` that has
  no Residual Motion calibrator
- warn once when the probe module returns a bare tensor (not timestep-conditioned)
- docs and tests: probe semantics, compile behaviour, true-CFG sigma, new guards

---------

Co-authored-by: DefTruth <qiustudent_r@163.com>

### [5b98ce2](https://github.com/vipshop/cache-dit/commit/5b98ce28b4a3cd2f18e88cf2253c1aa8b813f38f)

- **作者**: DefTruth
- **时间**: 2026-11-26T06:54:43Z
- **提交信息**: build(csrc): rename NVCC threads env var to CACHE_DIT_NVCC_THREADS (#1417)

The env name no longer describes the scope: after csrc was merged into a single `cache_dit._C_ops` extension, `--threads=` applies to every kernel family. No fallback to the old name.

Closes #1416

### [a6c256b](https://github.com/vipshop/cache-dit/commit/a6c256be825f94dec64159175c4f8fc57a00e02a)

- **作者**: DefTruth
- **时间**: 2026-11-26T06:26:30Z
- **提交信息**: fix(cp,logger): adopt torch 2.15 collectives API and filter Enum pytree notice (#1415)

* fix(cp): use all_gather_single on torch >= 2.15

* chore(logger): filter torch Enum pytree notice emitted by torchao imports

### [fc0a299](https://github.com/vipshop/cache-dit/commit/fc0a2991f8ba179d852397dec52a49d4418f24a3)

- **作者**: DefTruth
- **时间**: 2026-11-26T03:34:34Z
- **提交信息**: perf(ulysses): optimize FP8 stores and unify G16 defaults (#1413)

- Coalesce FP8 packed stores with aligned uint2 writes.
- Record rejected FP6 store and FP8 load width variants.
- Default FP4/FP6/FP8 communication to QKVO with per-group-16.
- Preserve explicit legacy granularities and validate FLUX standard/UAA paths.

### [7bd7130](https://github.com/vipshop/cache-dit/commit/7bd713094c18071c9b5691c95aa33e9eb194eee5)

- **作者**: DefTruth
- **时间**: 2026-11-26T03:32:01Z
- **提交信息**: perf(ulysses): coalesce FP4 packed stores (#1411)

- Pack each FP4 G16 payload into an aligned uint2 store.
- Reduce QKV quant store sectors and reach FP6-level Event latency.
- Preserve scalar fallbacks and packed numerical contracts.
- Document the rejected 128-bit shuffle variant and validation results.

### [59b5408](https://github.com/vipshop/cache-dit/commit/59b5408ad0bd2587fee06c11e416e14af233ea9c)

- **作者**: Butterfingrz
- **时间**: 2026-11-26T03:09:26Z
- **提交信息**: perf(h3): batch local VAE tiles and expose Pika video decode transforms (#1405)

- VAE-P decodes each rank's local tiles of a temporal window in one batched forward by default; opt out per instance with `vae._h3_vae_batch_local_tiles = False`
- Map group-relative tile ownership to global P2P peer IDs and propagate decode/stitch failures to all ranks before the next exchange
- Expose `PikaH3FlexVideoDecodeStep.denormalize_latents` / `postprocess` for the serving file path
- Add `bench/h3_media/bench_vae.py` and a CPU/Gloo test

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97651
- **最后更新**: 2026-11-27T02:03:21Z

## 提交统计

- **昨日提交总数**: 75
- **提交者数量**: 51
- **主要提交者**: linyafeng, Yizhou, Gyula Chinoradszki

## AI分析总结

# vLLM 昨日提交分析（共 75 个提交）

## 1. 主要更新类型分布
- **Bug 修复占比最高**，覆盖 KV 缓存、Rust 前端、多模态、结构化输出、分布式与工具调用解析等模块。
- **功能新增**：GDS KV 卸载、逐 attention group 卸载、`/health_generate` 健康检查端点、sparse_disk 权重传输后端、engram CPU 卸载。
- **性能优化**：QSA prefill FlashInfer 加速、HY4 融合算子、DCP logits 尺寸优化、LoRA split-K、Mamba 缓存状态降级。
- **CI/ROCm**：大量 AMD 平台修复与提速，含 MI300 任务迁移至 DPX、RDNA gfx1170/1171 支持。
- **重构与弃用**：移除 DBRX 死代码、弃用 `cudagraph_copy_inputs`、清理 Sleep Mode 冗余状态、权重传输懒加载工厂抽取。
- **安全加固**：tokenizer 选项保留、Jina 排序 prompt 限制、Cohere 模板限制三项修复。

## 2. 关键变更点与项目方向的关系
- **Rust 前端密集迭代**（约 15 条，由单一开发者主导）：统一请求校验、完善错误分类、对齐 OpenAI 兼容性（boolean 拼写、`original` 图像细节、tool 参数校验、Muse 工具名映射），并新增 admission_rejections 指标，表明项目正推动其走向生产就绪。
- **KV Offload 持续演进**：GDS 支持、CPU chunk 驱逐、P2P 跨 fetch 保留未消费 lookup 答案、EC runner 缓存命中后重新发布，服务长上下文场景并增强异构内存层级鲁棒性。
- **多硬件生态并进**：ROCm 修复量最大，另有 XPU、AITER、FlashInfer/Blackwell 优化，包括软限幅 logits 就地应用、UMBP 块清零、Muse Spark FP32 RoPE，体现对 CUDA 以外硬件的一等公民承诺。
- **模型正确性修复**：DeepSeek ViT 的 `cu_seqlens` 走 OOT attention 钩子、Qwen4Exp 的 QSA 缓存布局在 prefill/decode 间保持一致、Hunyuan A13B 以 token id 检测推理结束以正确应用结构化输出、DeepSeek V3.2 注意力序列并行与 ShardQ 解耦、mxfp8 scale swizzle 修复。
- **Hybrid/Mamba 与 agent 链路**：prefix-cache checkpoint、状态复制基准、decode 缓存修复；Inkling 长参数流式解析避免重复 re-parse，提升工具调用稳定性与延迟。

## 3. 对项目的影响与潜在意义
Rust 前端的 API 严格化与可观测性提升服务可靠性，为替代 Python 前端铺路；安全修复响应及时，有利于企业级部署。`/health_generate` 提供端到端生成就绪检查，对 K8s 编排价值显著。修复集中在边界条件与数值精度（就地操作、FP32 表保持、block zeroing 隔离），可减少静默精度退化与分布式竞态；CI 迁移加速 AMD 侧验证。模型与死代码精简降低维护负担，聚焦 Kimi-K3、HY4、Qwen、DeepSeek 等活跃模型，为后续版本聚焦核心能力奠定基础。

## 4. 值得关注的技术点
- **AI 协作开发常态化**：约七成提交含 Claude、Codex、Copilot、Cursor、vllm-agent 等署名，人机协作已深度融入开发流程。
- **就地（in-place）应用 soft cap/scale**：避免额外显存分配与同步开销。
- **`cu_seqlens` 路由至 out-of-tree attention 钩子**：体现插件化后端架构的扩展路径。
- 投机采样下首个 reasoning 边界保留的修复，关系结构化输出与推理模型的兼容性。

## 5. 对项目发展的整体影响
在 README 所述"易用、快速、低成本 LLM 服务"的愿景下，本批提交呈现"广度扩张 + 深度打磨"并行态势：横向拓宽硬件覆盖（ROCm/RDNA/Blackwell/XPU），纵向夯实多模态与 agent 推理链路正确性，同时推进 Rust 前端落地与 KV Offload 内存成本优化。这些工作虽多为质量巩固，却直接支撑 vLLM 在多样化硬件与复杂负载下的可信交付，是其保持主流推理引擎地位的基础。

## 详细提交记录

### [6710264](https://github.com/vllm-project/vllm/commit/6710264625beae682409712eb7791d4f1661752f)

- **作者**: Hugo Abonizio
- **时间**: 2026-11-26T22:58:25Z
- **提交信息**: [Perf][Qwen4Exp] Run QSA prefill steps with FlashInfer on Blackwell (#69735)

Signed-off-by: Hugo Abonizio <hugo.abonizio@gmail.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [da6aefd](https://github.com/vllm-project/vllm/commit/da6aefd315917ba2f8c68f11badddd719ecec8e7)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-26T22:47:12Z
- **提交信息**: [KV Connector][NIXL] Cut P/D loads at the Mamba prefix-cache checkpoint (#67064)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [f9d1824](https://github.com/vllm-project/vllm/commit/f9d1824a770f01e681fef8adb4b4bbe506e080aa)

- **作者**: Concurrensee
- **时间**: 2026-11-26T22:00:10Z
- **提交信息**: [ROCm][CI] Fix ViT backend and custom all-reduce tests with AITER on (#62524)

Signed-off-by: Yida Wu <yida.wu@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [43108ff](https://github.com/vllm-project/vllm/commit/43108ffccd6dfd1c1847fe30dad203374ef6582f)

- **作者**: Sardor Razikov
- **时间**: 2026-11-26T20:49:14Z
- **提交信息**: [ROCm][Bugfix] Pass is_ultraquant_run in automatic attention backend selection (#70169)

Signed-off-by: Sardor Razikov <161573062+SRKRZ23@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [54b5e7f](https://github.com/vllm-project/vllm/commit/54b5e7fa62e88382dd2324fe812e5757e0e50b1d)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-26T20:10:18Z
- **提交信息**: [ROCm][HY4] fp8_ds_mla with sinks, ShardQ and iHC sequence parallelism on ROCm (#70004)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9dad8f8](https://github.com/vllm-project/vllm/commit/9dad8f82cd8657dd87b7ea0610ed0d65dd4100c6)

- **作者**: Orkhan Huseynli
- **时间**: 2026-11-26T20:04:25Z
- **提交信息**: [Pre-commit][Bugfix] Move torch.cuda check into check_forbidden_strings (#69009)

Signed-off-by: Orkhan Huseynli <orkhan.huseyn@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d1cfc9d](https://github.com/vllm-project/vllm/commit/d1cfc9d2504cd728af4f7e8ef29dcdedbdd62543)

- **作者**: bogdan-petkovic
- **时间**: 2026-11-26T20:01:00Z
- **提交信息**: [ROCm][CI] Make the child stack dump work on Python 3.14 (#69911)

Signed-off-by: bogdan-petkovic <bpetkovi@amd.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [23f3dae](https://github.com/vllm-project/vllm/commit/23f3dae4aa1d4af355d7ddcf389c16b98e842599)

- **作者**: stefankoncarevic
- **时间**: 2026-11-26T19:58:19Z
- **提交信息**: [CI] Skip the global cleanup after kernel tests that skipped themselves (#70159)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [f60dc69](https://github.com/vllm-project/vllm/commit/f60dc69b96620ed1a48a668fc7243b51fa4e66f1)

- **作者**: stefankoncarevic
- **时间**: 2026-11-26T19:55:33Z
- **提交信息**: [CI][ROCm] Speed up the block-quant reference matmul in kernel tests (#70155)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [aae69ee](https://github.com/vllm-project/vllm/commit/aae69ee9c3f498e765d61195874bd1a0e24f78cd)

- **作者**: stefankoncarevic
- **时间**: 2026-11-26T19:53:37Z
- **提交信息**: [ROCm][CI] Use an fp32 lm_head for granite4_h in test_pp_tied_word_embeddings (#70134)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [16910e7](https://github.com/vllm-project/vllm/commit/16910e78dfb615347e88221441d7340c3d41f73e)

- **作者**: Luca Motz
- **时间**: 2026-11-26T19:36:17Z
- **提交信息**: [Bugfix][Transformers backend] Keep the BOS that the HF processor prepends (#70116)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [848b88c](https://github.com/vllm-project/vllm/commit/848b88cdebd0138786085e7cc347e32e4b34aecf)

- **作者**: Wentao Ye
- **时间**: 2026-11-26T19:18:55Z
- **提交信息**: [Refactor] Remove dead code in models (#69975)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [bd4cb51](https://github.com/vllm-project/vllm/commit/bd4cb514620aa3622116afb92d8e3a5178bda990)

- **作者**: Luca Motz
- **时间**: 2026-11-26T18:59:41Z
- **提交信息**: [Bugfix][Transformers backend] Don't split checkpoint tensors of skipped modules (#70076)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [6eb8194](https://github.com/vllm-project/vllm/commit/6eb8194d16f52aae9a27720987d3623e753c9d09)

- **作者**: Job Natdhanai
- **时间**: 2026-11-26T17:28:36Z
- **提交信息**: [Bugfix][Frontend] Keep the most likely candidate's logprob when /v1/completions top_logprobs keys collide (#65741)

Signed-off-by: spped2000 <spped2000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9d4029e](https://github.com/vllm-project/vllm/commit/9d4029eb2adbe6837812dc23ad820a4bbed7f8e2)

- **作者**: Sherif Waly
- **时间**: 2026-11-26T17:11:12Z
- **提交信息**: [Perf][DCP] Size sparse-indexer decode logits by the DCP-local context (#70178)

Signed-off-by: Sherif Waly <sherif.waly@mistral.ai>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [0b6be36](https://github.com/vllm-project/vllm/commit/0b6be36a75cf3ab7bdb7fd0a0133f2c3186ba918)

- **作者**: Dylan
- **时间**: 2026-11-26T16:41:27Z
- **提交信息**: [Rust Frontend] Serve /v1/decisions with next-token reads (#70031)

Signed-off-by: Dylan Chen <dylan@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cd08b4a](https://github.com/vllm-project/vllm/commit/cd08b4a144fe425ac7ecfe9747711db664bc05fd)

- **作者**: aoshen02
- **时间**: 2026-11-26T16:22:20Z
- **提交信息**: [Refactor][Sleep Mode] Remove unused SleepModeState and uncalled capability flags (#70038)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>

### [955da92](https://github.com/vllm-project/vllm/commit/955da92c65cf749b176f4866502c18dd5183c151)

- **作者**: Harry Mellor
- **时间**: 2026-11-26T15:43:59Z
- **提交信息**: [Deprecation] Deprecate `cudagraph_copy_inputs` and remove the compiler-managed input copy (#69675)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [955f85b](https://github.com/vllm-project/vllm/commit/955f85be04b6250d26e6915e26bdf6720fbc8258)

- **作者**: Harry Mellor
- **时间**: 2026-11-26T15:15:43Z
- **提交信息**: [Model] Remove DBRX (#70133)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a95fbda](https://github.com/vllm-project/vllm/commit/a95fbda2cd095ee59577ec2b7f5c077d86c64c73)

- **作者**: Shuolei Wang
- **时间**: 2026-11-26T15:11:12Z
- **提交信息**: [RL][Weight Transfer] Add sparse_disk backend for sparse deltas through storage (#69112)

Signed-off-by: Shuolei Wang <shuoleiwang123@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [62d538c](https://github.com/vllm-project/vllm/commit/62d538c61e69e760e74b65404d77bd44c778d8f6)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-26T14:46:56Z
- **提交信息**: [Bugfix][Kimi-K3] Composite transparent images over the checkpoint background (#69621)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [5446e33](https://github.com/vllm-project/vllm/commit/5446e33049e9457a1d86808b4fb69b494654e6d0)

- **作者**: Effi Ofer
- **时间**: 2026-11-26T14:41:51Z
- **提交信息**: [KV Offload] GDS kv offloading support (#66805)

Signed-off-by: Effi Ofer <effi.ofer@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [46e324e](https://github.com/vllm-project/vllm/commit/46e324e5827bcdabe84275a6caef070ba1be84ad)

- **作者**: liuzhenwei
- **时间**: 2026-11-26T14:15:28Z
- **提交信息**: [XPU][CI] Raise API Server Scale Out step timeout to 60 minutes (#70005)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [35e0e3c](https://github.com/vllm-project/vllm/commit/35e0e3c65cdda1183cdfdc381cc17fc324702f6d)

- **作者**: Ansat
- **时间**: 2026-11-26T14:05:06Z
- **提交信息**: [Bugfix][KV Cache] Fix Mamba decode resume caching a block that holds a later state (#70068)

Signed-off-by: Ansat <47277869+sansblues@users.noreply.github.com>

### [7d7d8a9](https://github.com/vllm-project/vllm/commit/7d7d8a9097127c08adf3980bcb9b8dd18834ec7a)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-26T14:05:00Z
- **提交信息**: [Core][Perf] Deprioritize superseded Mamba prefix-cache states (#69626)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Antigravity <noreply@google.com>

### [01eb54e](https://github.com/vllm-project/vllm/commit/01eb54eeb140cac834bad88a565239081afab00c)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-26T13:07:41Z
- **提交信息**: [Security] Reserve HF tokenizer options in chat requests (#69852)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [4af0937](https://github.com/vllm-project/vllm/commit/4af093713bc66972fe68f1455d7524f08724b1e6)

- **作者**: ChengYao-amd
- **时间**: 2026-11-26T12:54:21Z
- **提交信息**: [Bugfix][KV Offload] Offload the prompt tail of every attention group (#68836)

Signed-off-by: YaoCheng <Cheng.Yao2@amd.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [0f2069f](https://github.com/vllm-project/vllm/commit/0f2069ff8ace52c7434c4cceb068c27a9d27f654)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T12:45:15Z
- **提交信息**: [Rust Frontend] Classify multimodal preprocessing errors by fault (#70092)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [826d948](https://github.com/vllm-project/vllm/commit/826d94819c61ffab07474742e07e0af4955bd151)

- **作者**: linyafeng
- **时间**: 2026-11-26T12:35:38Z
- **提交信息**: [Bugfix][Structured Output] Preserve the first reasoning boundary in speculative drafts (#68112)

Signed-off-by: linnea-lin-00638949 <247557940+linnea-lin-00638949@users.noreply.github.com>
Co-authored-by: linnea-lin-00638949 <247557940+linnea-lin-00638949@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [239a764](https://github.com/vllm-project/vllm/commit/239a764b4127ed12a1f348c3381b4cc9815d6975)

- **作者**: Ganto12
- **时间**: 2026-11-26T12:27:56Z
- **提交信息**: [Bugfix][MoE] Swizzle mxfp8 activation scales after DP/EP dispatch for FlashInfer CUTLASS (#68814)

Signed-off-by: Ganto12 <20272171+Ganto12@users.noreply.github.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Wolfgang Welz <welzwo@gmail.com>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [9ab10c8](https://github.com/vllm-project/vllm/commit/9ab10c88f9130fa03164f2a9c8af408b4f503046)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T12:21:30Z
- **提交信息**: [Rust Frontend] Accept only OpenAI's input_audio format names (#70090)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [23b2463](https://github.com/vllm-project/vllm/commit/23b2463644a92119a98440afe64383e48120caa1)

- **作者**: Jee Jee Li
- **时间**: 2026-11-26T12:06:52Z
- **提交信息**: [Model][Perf] HY4: Use the fused iHC boundary op on all paths and fuse HY4 Flash q/kv-a projections (#69780)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [b935849](https://github.com/vllm-project/vllm/commit/b935849ce6450a9e660c04d6e41c83dc42a603c2)

- **作者**: noone-zhhh
- **时间**: 2026-11-26T11:55:26Z
- **提交信息**: [MM][CG] support ViT encoder cudagraph for DeepSeek-OCR2 (#64311)

Signed-off-by: noone-zhhh <workallday.zhh@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0312a89](https://github.com/vllm-project/vllm/commit/0312a89d33e1affe698d389d67cb9af1b4d12569)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T11:32:48Z
- **提交信息**: [Rust Frontend] Type renderer refusals of the request (#70091)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8ee3951](https://github.com/vllm-project/vllm/commit/8ee3951ecd39f1c1dcf5ce5dd476c0765fada149)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T11:17:42Z
- **提交信息**: [Rust Frontend] Reject non-object function tool parameters (#70089)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4f49b86](https://github.com/vllm-project/vllm/commit/4f49b860bbf5dbbed9527964d18a91799646fd4c)

- **作者**: Francesco Fusco
- **时间**: 2026-11-26T11:01:49Z
- **提交信息**: [Benchmark][Hybrid] Add a microbenchmark for the mamba state-copy kernel (#68206)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>
Co-authored-by: Claude <claude@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8901d8c](https://github.com/vllm-project/vllm/commit/8901d8ce7ec4c8c299df9a8f3cb5786a4a241ac5)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-26T10:59:13Z
- **提交信息**: [Security] Bound Jina ranking prompt preprocessing (#69967)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f202e4b](https://github.com/vllm-project/vllm/commit/f202e4b04bcaed4f62579a1bc6ab4e710374fa1a)

- **作者**: maithilijoshi20
- **时间**: 2026-11-26T10:57:26Z
- **提交信息**: [KV Offload] Prefer eviction of non-retained CPU chunks (#70026)

Signed-off-by: maithilijoshi20 <maithilij2003@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0ebeecc](https://github.com/vllm-project/vllm/commit/0ebeecc358251834f3aef3c9ba8c2d249d38cc67)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T10:44:32Z
- **提交信息**: [Rust Frontend] Return empty logprobs for chat and generate requests aborted during prefill (#70095)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f5f4d06](https://github.com/vllm-project/vllm/commit/f5f4d061d847513b5ab9e5df530e3858903d3c40)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T10:43:52Z
- **提交信息**: [Rust Frontend] Accept Python's inverse spellings of boolean flags (#70096)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [20122dc](https://github.com/vllm-project/vllm/commit/20122dc83b9dfaf9b1c5b74bc9a54c6a01c5ae7b)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T10:43:10Z
- **提交信息**: [Rust Frontend] Bound allowed_token_ids by the model vocabulary (#70093)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [62c93a7](https://github.com/vllm-project/vllm/commit/62c93a7bc13d4354e12f27a9b45e81827e3411cb)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T10:40:24Z
- **提交信息**: [Rust Frontend] Resolve parser selections at model load and refuse unusable explicit ones (#69614)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8f3cbd8](https://github.com/vllm-project/vllm/commit/8f3cbd8791f54e4ef1fb23d50b65d0d9598299d8)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T10:40:10Z
- **提交信息**: [Rust Frontend] Warn about a packaged vllm-rs built without the checkout's rust/ changes (#69382)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e4ac319](https://github.com/vllm-project/vllm/commit/e4ac319d203f3dad675d71b0b36e35e293ec291f)

- **作者**: Dylan
- **时间**: 2026-11-26T09:54:33Z
- **提交信息**: [Rust Frontend] Count vllm:admission_rejections (#69856)

Signed-off-by: Dylan Chen <dylan@inferact.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cd2c8a3](https://github.com/vllm-project/vllm/commit/cd2c8a33dee51f194b6b50399c6953da192e8532)

- **作者**: Rabinovich
- **时间**: 2026-11-26T09:53:25Z
- **提交信息**: [Bugfix][Rust Frontend] Accept "original" image detail (#70001)

Signed-off-by: Yixiao Zeng <yixiaozeng0208@outlook.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b562dec](https://github.com/vllm-project/vllm/commit/b562deca652a00a41e5066dd986ac2e5dec30a9e)

- **作者**: Divakar Verma
- **时间**: 2026-11-26T09:42:45Z
- **提交信息**: [CI][ROCm] Transcendental, reduction and MFMA bounds for specialized decode (T1 of #68016) (#67977)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a19af6d](https://github.com/vllm-project/vllm/commit/a19af6de9bc25bc2128e8c0e687e44fc28f329b4)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-26T09:36:51Z
- **提交信息**: [Security] Restrict inline request templates in Cohere serving (#69969)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a9b678a](https://github.com/vllm-project/vllm/commit/a9b678aab0a5dd85d867eb07675c0dc092b8abec)

- **作者**: Sumanth R Hegde
- **时间**: 2026-11-26T09:33:15Z
- **提交信息**: [Core] Add a generation readiness check `/health_generate` (#60505)

Signed-off-by: liofranxx <liofranxx@99-1-180-7.lightspeed.clmasc.sbcglobal.net>
Signed-off-by: SumanthRH <sumanthrh99@gmail.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: liofranxx <liofranxx@99-1-180-7.lightspeed.clmasc.sbcglobal.net>
Co-authored-by: lio <101571019+lio1226@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [4fd2495](https://github.com/vllm-project/vllm/commit/4fd24951cc374300b8172debd2e550863ce7115b)

- **作者**: Isotr0py
- **时间**: 2026-11-26T09:04:22Z
- **提交信息**: [Fast Start] Add engram cpu offloading support for preload daemon (#69627)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [11fac67](https://github.com/vllm-project/vllm/commit/11fac67e35e4d557f7bf90da5863449f592336f2)

- **作者**: maithilijoshi20
- **时间**: 2026-11-26T08:55:33Z
- **提交信息**: [Bugfix][Multimodal] Honor Gemma 4 image resize settings (#67168)

Signed-off-by: maithilijoshi20 <maithilij2003@gmail.com>

### [5b6dfcc](https://github.com/vllm-project/vllm/commit/5b6dfccf5daee0f636aefefd44d9b70e038c2b8f)

- **作者**: Chauncey
- **时间**: 2026-11-26T08:51:43Z
- **提交信息**: [Perf] Decouple DeepSeek V3.2 attention sequence parallelism from ShardQ (#68074)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [799bb49](https://github.com/vllm-project/vllm/commit/799bb49c25f6a8cfdde2c85385ac28414c28c1d3)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-26T08:49:59Z
- **提交信息**: [ROCm][Kimi-K3] Log the SiTUv2 MoE activation mode and correct the recipe note (#69625)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [7ee2209](https://github.com/vllm-project/vllm/commit/7ee22092ac2d5390cc274609e02c93bc8ecd89aa)

- **作者**: Or Ozeri
- **时间**: 2026-11-26T08:49:23Z
- **提交信息**: [Bugfix][KV Offload] Revert "Return pending work, events and stats from on_schedule_end (#68962)" (#70063)

Signed-off-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5b5b371](https://github.com/vllm-project/vllm/commit/5b5b371e3217550c79da02b8dd8bd3f1e3859324)

- **作者**: liuzhenwei
- **时间**: 2026-11-26T08:18:31Z
- **提交信息**: [Bugfix] Avoid importing ROCm platform in AITER W4A16 support check on non-ROCm (#70009)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [711126c](https://github.com/vllm-project/vllm/commit/711126ce6846b1d42f0ff3b1333f9a506a5db3d5)

- **作者**: Reid
- **时间**: 2026-11-26T08:16:41Z
- **提交信息**: [Bugfix][Rust Frontend] Recover from per-peer ZMQ errors (#67945)

Signed-off-by: reidliu41 <reid201711@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [632ba4f](https://github.com/vllm-project/vllm/commit/632ba4f90cb3fe67f6be28ff97f57a7ef7156258)

- **作者**: Darsh Patel
- **时间**: 2026-11-26T07:51:26Z
- **提交信息**: [Rust Frontend] Implement engine-free raw-JSON gRPC Render RPC (#65503) (#67700)

Signed-off-by: darshpatel1052 <b23ee1052@iitj.ac.in>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [98449f6](https://github.com/vllm-project/vllm/commit/98449f6218a7a641ecd9e1b55b6c24bb467df57a)

- **作者**: Jee Jee Li
- **时间**: 2026-11-26T07:48:46Z
- **提交信息**: [Doc][Misc] Make the --monokernel docstring model and hardware agnostic (#70070)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [7bca9fa](https://github.com/vllm-project/vllm/commit/7bca9fafe294884cc45ee5a2da202eb0125cbfed)

- **作者**: Yicong Wang
- **时间**: 2026-11-26T07:27:54Z
- **提交信息**: [Bugfix][Mooncake] Reject missing draft context KV (#69870)

Signed-off-by: wangyicong <wangyicong@bytedance.com>

### [353d5fe](https://github.com/vllm-project/vllm/commit/353d5febf7379b0459020c4341a9ffac58997650)

- **作者**: Bugen Zhao
- **时间**: 2026-11-26T06:40:31Z
- **提交信息**: [Rust Frontend] Consolidate request validation, retire `validator`, and complete `Error::param()` (#68933)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5d561d9](https://github.com/vllm-project/vllm/commit/5d561d9860cf6e7f194b07f1503bcd0180cccff3)

- **作者**: Taoyu Zhu
- **时间**: 2026-11-26T06:11:20Z
- **提交信息**: [Bugfix][KV Offload] Requeue CPU prefixes tail first in SimpleCPUOffload (#67952)

Signed-off-by: Taoyu Zhu <zhutaoyu97@gmail.com>
Signed-off-by: Dakai An <dakaian108@gmail.com>
Signed-off-by: Taoyu Zhu <z609495@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e3279d6](https://github.com/vllm-project/vllm/commit/e3279d678490e523f02744681b30f88465f6c635)

- **作者**: Yizhou
- **时间**: 2026-11-26T06:03:42Z
- **提交信息**: [Bugfix] Route DeepSeek ViT cu_seqlens through the OOT attention hook (#70044)

Signed-off-by: Yizhou <136800916+yiz-liu@users.noreply.github.com>

### [5aea305](https://github.com/vllm-project/vllm/commit/5aea30579ad672c3c35be43112b7a1f7b293a09e)

- **作者**: bogdan-petkovic
- **时间**: 2026-11-26T05:53:54Z
- **提交信息**: [Bugfix] Apply soft cap and scale in place in get_top_tokens (#69898)

Signed-off-by: bogdan-petkovic <bpetkovi@amd.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [a484522](https://github.com/vllm-project/vllm/commit/a48452235e9be36d348f60386ad49f5fb9514442)

- **作者**: Sheral Kumar
- **时间**: 2026-11-26T05:30:30Z
- **提交信息**: [ROCm][CI] Move MI300 Quantization, MoE, distributed, and batch invariance jobs to DPX (#69952)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f73f588](https://github.com/vllm-project/vllm/commit/f73f58869b4abc1a2b0a88d7db46dde367efe1b4)

- **作者**: liranschour
- **时间**: 2026-11-26T04:59:25Z
- **提交信息**: [Bugfix][KV Offload][P2P] Keep unconsumed lookup answers across a fetch (#68660)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [87ccca3](https://github.com/vllm-project/vllm/commit/87ccca3d364c4623eacdff482510ab2b8093cc42)

- **作者**: Harry Huang
- **时间**: 2026-11-26T04:54:50Z
- **提交信息**: [Qwen4Exp] Keep QSA cache layouts consistent across prefill and decode (#69882)

Signed-off-by: huanghaoyan.hhy <huanghaoyan.hhy@alibaba-inc.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6ed3615](https://github.com/vllm-project/vllm/commit/6ed3615cf6a3cb7921a26bc3d59949a789fd2bf8)

- **作者**: Gyula Chinoradszki
- **时间**: 2026-11-26T04:30:52Z
- **提交信息**: [Bugfix][UMBP] Keep synchronous load blocks out of block zeroing (#69656)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [72fab49](https://github.com/vllm-project/vllm/commit/72fab49ea5bef3e1ea66c2e019aeaa0032ab7fb8)

- **作者**: bogdan-petkovic
- **时间**: 2026-11-26T03:53:48Z
- **提交信息**: [Bugfix] Apply the logits soft cap in place (#69674)

Signed-off-by: bogdan-petkovic <bpetkovi@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a53e0a0](https://github.com/vllm-project/vllm/commit/a53e0a05167117aaf671e7c10d2b91a9fa0c88a3)

- **作者**: Shuhan Zhang
- **时间**: 2026-11-26T03:21:43Z
- **提交信息**: [Perf][LoRA] Avoid empty split-K programs in shrink (#61087)

Signed-off-by: Manifold68575 <14250491@cumt.edu.cn>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [89c908a](https://github.com/vllm-project/vllm/commit/89c908a1b81c0b1826260818e60668c99a577642)

- **作者**: medunes
- **时间**: 2026-11-26T03:11:44Z
- **提交信息**: [Bugfix][Parser] Stream long Inkling tool arguments without re-parsing (#69297)

Signed-off-by: medunes <medunes@protonmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [15c90d1](https://github.com/vllm-project/vllm/commit/15c90d1a8dc0cc2cd2e045a13f9c521e92690ab5)

- **作者**: Uros Markovic
- **时间**: 2026-11-26T03:02:40Z
- **提交信息**: [ROCm][RDNA] Add gfx1170 and gfx1171 support (#65202)

Signed-off-by: Uros Markovic <umarkovi@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [c99bc0a](https://github.com/vllm-project/vllm/commit/c99bc0ae570369e497a834b58219e7f8b2407a81)

- **作者**: Harshee Jignesh Shah
- **时间**: 2026-11-26T03:02:20Z
- **提交信息**: [Bugfix][Reasoning] Hunyuan A13B: detect reasoning end from token ids so structured output applies (#63632)

Signed-off-by: helephants <harsheejshah@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [13c850c](https://github.com/vllm-project/vllm/commit/13c850cb622ffb97a067863f470486de8fdfa5a7)

- **作者**: aoshen02
- **时间**: 2026-11-26T02:26:44Z
- **提交信息**: [Refactor][Weight Transfer] Extract shared _LazyEngineFactory base class (#69926)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>

### [014649a](https://github.com/vllm-project/vllm/commit/014649a2c8c5aa176f144b6520a4d15b568d5c21)

- **作者**: Alon H
- **时间**: 2026-11-26T02:00:34Z
- **提交信息**: [Bugfix][Tool Parser][Rust Frontend] Muse: map `<tool>.<suffix>` back to a registered bare tool (#67972)

### [04ffa45](https://github.com/vllm-project/vllm/commit/04ffa45884dc7c956904ce8723b86e0b48acbd3d)

- **作者**: fanxingran
- **时间**: 2026-11-26T01:54:36Z
- **提交信息**: [Bugfix][Muse Spark] Keep the FP32 RoPE tables in FP32 (#63078)

Signed-off-by: fanxingran <xingran.fan@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Matt <156021403+mawong-amd@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [5ddf53f](https://github.com/vllm-project/vllm/commit/5ddf53fb5287fe15b5d7e70732dfd92f81636e97)

- **作者**: rebel-eunji
- **时间**: 2026-11-26T01:09:46Z
- **提交信息**: [Bugfix][EC] Republish runner cache hits after CPU-tier eviction (#65123)

Signed-off-by: rebel-eunji <eunji.lee@rebellions.ai>
Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-27
**监控日期**: 2026-11-26
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7982
- **最后更新**: 2026-11-27T02:31:00Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 21
- **主要提交者**: Tianyao Wu, Alessio Netti, Sheng GAO

## AI分析总结

# vllm-omni 昨日提交分析（28笔）

## 1. 主要更新类型
- **Bug修复**：约10笔，占比最高（ROCm兼容、full-payload原子性、CI稳定性）
- **性能优化**：约6笔（Ulysses通信、TTS批处理、模型权重缓存、Ascend推理）
- **功能新增**：约7笔（新模型集成、机器人策略契约、采样器、批处理参数扩展）
- **文档/CI**：约5笔（README、PR评审规范、测试图确定性释放）

## 2. 关键变更点及与项目方向的关系
- **全双工语音交互深化**：MiniCPM-o跨插话记忆、InternLM Sage-Interaction全双工、Confucius4-TTS与Kimi-Audio新模型接入——直接支撑"全模态服务"核心定位
- **扩散模型性能线**：Ulysses all-to-all自动选择、CE overlap精确性验证、SANA-WM反向GDN扫描优化——强化Diffusion serving竞争力
- **多硬件生态**：大量ROCm/MI300修复（NIXL/Mooncake加载、FNUZ FP8量化）+ Ascend MRv2优化，扩大硬件覆盖面
- **Robotic新领域**：Phase 1机器人策略服务契约（#8249），暗示项目向具身智能服务扩展的探索

## 3. 影响与潜在意义
- **稳定性显著提升**：full-payload原子性与失败传播（#11243/#10778）解决分布式传输的一致性隐患，对生产部署意义重大
- **ROCm成熟度**：连续5笔ROCm修复表明AMD平台正从"可用"走向"可靠"，MI300成为一等公民
- **性能调优精细化**：generation_min_batch_size等参数扩展（#9809）与Modulation缓存（#7529）体现从粗放优化转向细粒度调参

## 4. 值得关注的技术点
- `ulysses_a2a_backend=auto`：通信后端自动选择，降低用户配置门槛
- Qwen-Image串行CFG分支间modulation复用：典型的时间换空间缓存策略
- 运行时逐kernel验证CE overlap精确性：性能优化不牺牲正确性的工程范式
- 部分提交引入Claude/Cursor作为co-author，反映AI辅助开发在核心仓库的常态化

## 5. 对项目发展的意义
结合README"Easy, fast, cheap omni-modality serving"的目标，本批提交呈现三条主线：**模态覆盖持续扩张**（TTS/全双工/机器人策略）、**性能与稳定性双轮驱动**（通信优化+原子性保障）、**多硬件平台铺开**（CUDA/ROCm/Ascend）。项目正从功能堆叠期进入工程化成熟期，全双工交互和Diffusion serving是当前投入最重的差异化方向，而ROCm支持的密集修复则为跨平台商业化铺路。总体看，这些提交将推动vllm-omni向更可靠、更易用、更广覆盖的全模态服务平台演进。

## 详细提交记录

### [d62b6be](https://github.com/vllm-project/vllm-omni/commit/d62b6beadd36883d440aa21704d0477b031ced4f)

- **作者**: Hongsheng Liu
- **时间**: 2026-11-26T23:29:53Z
- **提交信息**: [Docs] Update the README slides link for v0.34.0 (#11209)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [6c30b6e](https://github.com/vllm-project/vllm-omni/commit/6c30b6eb7f5e69407b5353be4f806e0bfc7a96fb)

- **作者**: SYLAR
- **时间**: 2026-11-26T23:04:32Z
- **提交信息**: [Perf][Diffusion] Ulysses: pick the all-to-all transport automatically (`ulysses_a2a_backend=auto`) (#11109)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [95b4030](https://github.com/vllm-project/vllm-omni/commit/95b4030afd7088abf9490c5d9196ca4aee68341f)

- **作者**: Xieyancheng
- **时间**: 2026-11-26T22:05:13Z
- **提交信息**: [Frontend] Add Phase 1 robot policy serving contract and validation (#8249)

Signed-off-by: Xieyancheng <862049654@qq.com>

### [c9f0b38](https://github.com/vllm-project/vllm-omni/commit/c9f0b3839ff8842b16de3914ca05d02f1492a98e)

- **作者**: lm10-arg
- **时间**: 2026-11-26T20:26:50Z
- **提交信息**: [Bugfix] Keep full-payload generation inputs atomic (#11243)

Signed-off-by: lm10-arg <linluo@icloud.com>

### [1c2760f](https://github.com/vllm-project/vllm-omni/commit/1c2760fa15c789ca57b2fe559ab9bed0756b9ca8)

- **作者**: dongbo910220
- **时间**: 2026-11-26T20:12:52Z
- **提交信息**: [Kernel] Optimize SANA-WM reverse GDN scans (#7485)

Signed-off-by: dongbo910220 <1275604947@qq.com>

### [8a5c185](https://github.com/vllm-project/vllm-omni/commit/8a5c185c1de346a0c1b7aed0bacd7d8d064957e1)

- **作者**: dongbo910220
- **时间**: 2026-11-26T20:12:24Z
- **提交信息**: [Model] Cache Qwen-Image modulation across serial CFG branches (#7529)

Signed-off-by: dongbo910220 <1275604947@qq.com>

### [47a9f26](https://github.com/vllm-project/vllm-omni/commit/47a9f2672e3a2af26b227ea059a045d9c4930289)

- **作者**: BeatSeat
- **时间**: 2026-11-26T20:01:28Z
- **提交信息**: [Model][Perf] IndexTTS 2 & 2.5: Default MRv2 Deploy Configs, Batched S2Mel Concurrency Fixes, and Scoped TF32 (#8787)

Signed-off-by: BeatSeat <wendavid552@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Sy03 <1370724210@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [6bb304c](https://github.com/vllm-project/vllm-omni/commit/6bb304c1d58611264b9e241559d90ebd1f55e5e3)

- **作者**: lm10-arg
- **时间**: 2026-11-26T19:25:41Z
- **提交信息**: [Bugfix][ROCm] Load NIXL and Mooncake on ROCm and add MI300 distributed connector coverage (#11235)

Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [af55026](https://github.com/vllm-project/vllm-omni/commit/af5502660ce8afcf84981d8e321177dc4c023010)

- **作者**: Alessio Netti
- **时间**: 2026-11-26T19:24:15Z
- **提交信息**: [Feat] Extend generation_min_batch_size and related knobs for batch coalescing (#9809)

Signed-off-by: Alessio Netti <26897207+AlessioNetti@users.noreply.github.com>

### [1999347](https://github.com/vllm-project/vllm-omni/commit/199934705adcdf9a96a0b77ba43713922174a636)

- **作者**: step-out
- **时间**: 2026-11-26T19:00:32Z
- **提交信息**: [Misc][Doc] Add Duplex-MPE multi-party full-duplex selective participation benchmark (#11156)

Signed-off-by: Chengqian Ma <machengqian25@stu.pku.edu.cn>

### [43eb3a1](https://github.com/vllm-project/vllm-omni/commit/43eb3a17205bde6e3001b870da0fe9d13cd1a516)

- **作者**: SFA_Sukhoi
- **时间**: 2026-11-26T18:21:51Z
- **提交信息**: [Bugfix] Restore Audio8 TTS frame generation and RAS on MRv2 (#11190)

Signed-off-by: beiningwu <sukhoi258@163.com>
Co-authored-by: beiningwu <sukhoi258@163.com>

### [e557696](https://github.com/vllm-project/vllm-omni/commit/e5576969e12c878a9e4c0e9f5ea0a5b4884ce37c)

- **作者**: NumberWan
- **时间**: 2026-11-26T17:41:07Z
- **提交信息**: [Bugfix] Fail the request when a full-payload stage transfer cannot succeed (#10778)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: NATURE <wzliu@connect.hku.hk>

### [b134973](https://github.com/vllm-project/vllm-omni/commit/b1349733eb4bc7c3734eb046240cb32444eaa54c)

- **作者**: lm10-arg
- **时间**: 2026-11-26T17:19:39Z
- **提交信息**: [Bugfix][CI/Build][ROCm] Stabilize LongCat tiny-diffusion startup (#11236)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Signed-off-by: lm10-arg <linluo@icloud.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [0bc0d7c](https://github.com/vllm-project/vllm-omni/commit/0bc0d7c0adb1497dda8c9333088977792f2b9eb1)

- **作者**: lm10-arg
- **时间**: 2026-11-26T16:36:22Z
- **提交信息**: [CI/Build][CUDA] Release MOSS test graph deterministically (#11240)

Signed-off-by: lm10-arg <linluo@icloud.com>

### [367a702](https://github.com/vllm-project/vllm-omni/commit/367a702abbe212899b0c9202dceeb29a34605605)

- **作者**: lm10-arg
- **时间**: 2026-11-26T13:38:29Z
- **提交信息**: [Bugfix][ROCm] Fix FNUZ FP8 in Cosmos3/HSDP and add MI300 diffusion quantization and Wan2.2 AutoRound coverage (#11193)

Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d270464](https://github.com/vllm-project/vllm-omni/commit/d27046415d5652b755c19e4654b56a341f8b9250)

- **作者**: 汪志鹏
- **时间**: 2026-11-26T11:57:23Z
- **提交信息**: [Refactor][Diffusion] MiniMax-H3: every weight set serves control, continuation, editing and guides (#11078)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [1ee823b](https://github.com/vllm-project/vllm-omni/commit/1ee823b243ddfb6198fa9e1877ed123d1e73a7c5)

- **作者**: wangqiankun13
- **时间**: 2026-11-26T11:55:13Z
- **提交信息**: [CI/Build][Bugfix] Fix HunyuanImage3 sharing startup and run TP2 E2E locally (#10431)

Signed-off-by: wangqiankun <wangqiankun13@huawei.com>

### [4131145](https://github.com/vllm-project/vllm-omni/commit/41311458ac908219748fe3fb4869070e6e7f1d15)

- **作者**: SYLAR
- **时间**: 2026-11-26T10:43:31Z
- **提交信息**: [Perf][Diffusion] Ulysses CE overlap: verify exactness at runtime per attention kernel and shape (#11163)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9d2fd5d](https://github.com/vllm-project/vllm-omni/commit/9d2fd5d3148fe238509cde04c90c18eecfb990d5)

- **作者**: Tianyao Wu
- **时间**: 2026-11-26T10:29:20Z
- **提交信息**: [MiniCPM-o] Remember the conversation across duplex barge-ins (#10000)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [00f8ac7](https://github.com/vllm-project/vllm-omni/commit/00f8ac7a24f00eb62c302a28b1103f40da57f8d1)

- **作者**: wuli666
- **时间**: 2026-11-26T07:07:33Z
- **提交信息**: [Model] Add InternLM Sage-Interaction full-duplex support (#11164)

Signed-off-by: wuli666 <421774554@qq.com>

### [dc945ca](https://github.com/vllm-project/vllm-omni/commit/dc945ca8f4fb8b363b3e8696410aced593c033f0)

- **作者**: nodeeeeee
- **时间**: 2026-11-26T06:37:33Z
- **提交信息**: [Feature][Diffusion] Add the DPM++ 2M sampler for MiniMax H3 (#10405)

Signed-off-by: nodeeeeee <zhangkai.nodeee@gmail.com>

### [94de758](https://github.com/vllm-project/vllm-omni/commit/94de758f0678bb8d5e770349c463f1f267a91f20)

- **作者**: y-null
- **时间**: 2026-11-26T05:51:20Z
- **提交信息**: [Hardware][Ascend][perf] Optimize MiniCPM-o MRv2 speech serving (#10595)

Signed-off-by: y_null <y_null@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [8c6fb4a](https://github.com/vllm-project/vllm-omni/commit/8c6fb4a1d48eaec4d0694d4b7dc97a4d7a5421af)

- **作者**: Chaoying
- **时间**: 2026-11-26T04:52:48Z
- **提交信息**: [Model] Add Confucius4-TTS support (#10906)

Signed-off-by: linchaoying6 <linchaoying6@jd.com>
Co-authored-by: linchaoying6 <linchaoying6@jd.com>

### [0357ef3](https://github.com/vllm-project/vllm-omni/commit/0357ef322ea3b5d641744c1e32cda097c6ad68a2)

- **作者**: WeiQing Chen
- **时间**: 2026-11-26T03:39:33Z
- **提交信息**: [Doc] Add evidence-based scoring to PR reviews (#11141)

Signed-off-by: David Chen <530634352@qq.com>
Co-authored-by: Isotr0py <41363108+Isotr0py@users.noreply.github.com>

### [14ce3d8](https://github.com/vllm-project/vllm-omni/commit/14ce3d89dd83812446126874286e2c6738d58c32)

- **作者**: lm10-arg
- **时间**: 2026-11-26T03:29:50Z
- **提交信息**: [Bugfix][ROCm] Qualify tiny-diffusion determinism, LTX2 and AITER compile on MI300 (#11176)

Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3af5468](https://github.com/vllm-project/vllm-omni/commit/3af5468c1be66dfe97a751bdf65cb9fc13a20ea9)

- **作者**: Aochang Liu
- **时间**: 2026-11-26T02:53:30Z
- **提交信息**: [Feature][New Model]Add Kimi-Audio model integration (#7383)

Signed-off-by: HelloWorldU <asd001liu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [101ca6f](https://github.com/vllm-project/vllm-omni/commit/101ca6f5172397c74d8bc7b31abf406610d04e7a)

- **作者**: Sheng GAO
- **时间**: 2026-11-26T02:29:08Z
- **提交信息**: [CI/Build][Bugfix] Fix LTX-2.5 official full-attention RoPE width (#11002)

Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [db96e6d](https://github.com/vllm-project/vllm-omni/commit/db96e6d4a0420c81a270f1538b642185d677ced8)

- **作者**: Howard Yang
- **时间**: 2026-11-26T01:48:55Z
- **提交信息**: [Model] MiniCPM-o 4.5 Thinker-only full duplex: project Stage 0 as text (#10315)

Signed-off-by: maithilijoshi20 <97733343+maithilijoshi20@users.noreply.github.com>
Signed-off-by: HowardYangAI <13777842855@163.com>
Co-authored-by: maithilijoshi20 <97733343+maithilijoshi20@users.noreply.github.com>

---
