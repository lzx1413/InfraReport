# GitHub Stars 合并报告 - 2026-08-02

**合并日期**: 2026-08-03
**监控日期**: 2026-08-02
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


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2118
- **最后更新**: 2026-08-02T03:27:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2557
- **最后更新**: 2026-08-02T19:32:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2182
- **最后更新**: 2026-08-01T08:47:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6083
- **最后更新**: 2026-08-02T20:52:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3908
- **最后更新**: 2026-08-02T22:07:50Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Suhaan Khurana, KyleNeverGivesUp, William Lin

## AI分析总结

根据仓库README背景和提交记录，本次更新属于工程完善与稳定性提升，主要情况如下：

### 1. 主要更新类型
- **Bug修复**：2项，涉及 Gemma 连接器 token 对齐问题、验证流程中文本编码器配置丢失问题。
- **重构优化**：1项，针对注意力后端（attention backend）的解析时机进行调整。
- **代码整理**：1项，统一数据集下载脚本到 `examples/datasets/` 目录。

### 2. 关键变更点与项目方向的关系
- **注意力后端解析优化**：将后端选择从“重复解析”改为“组件加载时一次性解析”，减少了运行期开销和潜在的不一致。FastVideo 这类视频生成框架对训练/推理性能敏感，此改动直接服务于高效执行。
- **Gemma 连接器 token 左对齐**：修复批量（batch）处理时多行 token 对齐的边界情况，确保多模态文本嵌入的准确性，是文本-视频生成链路中的关键正确性保证。
- **验证流程保留 loader 填充的文本编码器配置**：防止训练时配置信息在验证阶段丢失，保证训练与验证行为一致，对可靠评测结果很重要。
- **数据集脚本统一整理**：规范化示例代码结构，提升项目可读性与用户上手体验。

### 3. 对项目的影响与潜在意义
- 提升**框架稳定性**，尤其在大 batch 训练、验证循环和多模态文本编码等核心场景。
- 通过减少注意力后端的重复解析，带来一定的**运行时效率提升**，有利于长视频/大规模训练任务。
- 整理示例脚本降低了**新用户的使用门槛**，符合项目提供快速开始和文档的定位。

### 4. 值得关注的技术点
- **后端解析时机的设计**：关注点在“加载时”还是“每次前向时”对性能的差异，体现了对大规模模型推理开销的精细考量。
- **Gemma 连接器的 token 对齐方式**：涉及多模态模型对文本序列维度的处理，是保证模型正确理解提示词的关键细节。
- **配置生命周期管理**：如何从数据加载器到验证 pipeline 保持配置一致，是框架 API 设计的重要环节。

### 5. 对项目发展的影响（结合 README 背景）
FastVideo 定位为面向视频生成的高效训练/推理框架，此次提交虽无重大新功能，但聚焦**稳定、高效、易用**三个层面：
- 修复边界问题有助于建立用户对框架的信任；
- 性能相关重构为更大规模视频生成任务铺路；
- 示例

## 详细提交记录

### [7b094c9](https://github.com/hao-ai-lab/FastVideo/commit/7b094c945b6c0f24f7cf25a8565ce724d0aa1115)

- **作者**: William Lin
- **时间**: 2026-08-02T22:07:42Z
- **提交信息**: [refactor]: resolve attention backend once per component at load time (#1657)

### [eeb3e8a](https://github.com/hao-ai-lab/FastVideo/commit/eeb3e8a597ae816942e8816a8d97d90336e4590f)

- **作者**: William Lin
- **时间**: 2026-08-02T22:01:34Z
- **提交信息**: [bugfix]: left-align Gemma connector tokens per batch row (#1664)

### [05406c5](https://github.com/hao-ai-lab/FastVideo/commit/05406c5d1b33b9ad76b1f6b474a92f2d67b3e20d)

- **作者**: Suhaan Khurana
- **时间**: 2026-08-02T21:21:24Z
- **提交信息**: [misc]: consolidate dataset download scripts under examples/datasets/ (#1667)

### [99d04a7](https://github.com/hao-ai-lab/FastVideo/commit/99d04a7f98258769f20bb1a9d27eb8f68e5e0053)

- **作者**: KyleNeverGivesUp
- **时间**: 2026-08-02T21:10:16Z
- **提交信息**: [bugfix] keep loader-populated text encoder configs in the validation pipeline (#1669)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34218
- **最后更新**: 2026-08-02T21:28:50Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: YiYi Xu

## AI分析总结

好的，我来分析这条提交记录。

## 1. 主要更新类型
**Bug 修复 + 功能增强**。核心是修复自动卸载（auto offloading）与组卸载（group offloading）两种机制无法协同工作的缺陷，并引入新的策略接口。

## 2. 关键变更点
- **修复机制冲突**：此前 `enable_auto_cpu_offload`（来自 accelerate 的 `_hf_hook`）与 `enable_group_offload`（diffusers 的 `HookRegistry`）是两个互不感知的独立钩子系统。同时开启时，自动卸载通过调用 `.to()` 释放内存，但组卸载模块会拒绝该操作并仅发出警告——导致自动卸载管理器记录的"已释放内存"实际并未释放，且错误地将组卸载模型的全部权重计入显存占用（实际上每组只有一份驻留）。
- **组卸载模型参与自动卸载**：现在组卸载模型可以参与自动卸载流程，但由它自己决定如何腾出空间（通过 `pre_forward` 咨询策略），而不是被管理器强制卸载，避免无效操作。
- **新增 `offload_strategy` 参数**：由于内存估算无法准确描述组卸载场景，`enable_auto_cpu_offload` 新增 `offload_strategy` 参数，`set_offload_strategy` 可在之后动态替换。默认的 `AutoOffloadStrategy` 基于模型内存足迹做决策，当遇到组卸载时会发出警告（仅当用户未显式传入策略时）。

## 3. 对项目的影响和潜在意义
- **提升混合场景可靠性**：修复了两种优化机制共存时的静默内存管理失效问题，避免用户在启用组卸载后误以为自动卸载生效，实际却遭遇 OOM 或内存泄漏。
- **释放组合式优化的可能性**：此前用户只能在"组卸载"和"自动卸载"间二选一，现在可以安全地叠加使用，为大规模模型推理（如多 GPU 或 CPU+GPU 混合推理）提供更灵活的内存控制手段。
- **引入可扩展策略框架**：`offload_strategy` 接口允许社区自定义卸载决策逻辑，为后续针对组卸载场景的专用策略（如感知每组实际驻留量的策略）留出空间。

## 4. 值得关注的技术点
- **抽象层次设计**：将"卸载什么"与"如何卸载"解耦——组卸载模型可以自行决定放置位置，管理器不再越俎代庖，体现了良好的职责分离。
- **兼容性处理**：两种启用的先后顺序（先组卸载再自动卸载，或反之）都可以正常工作，确保 API 的灵活性。
- **安全预警机制**：当内存估算依据与实际情况不符时，用警告而不是静默失败来提醒用户，避免误导性行为。

## 5. 对项目发展的影响
diffusers 定位为最易用的扩散模型工具库，其推理优化能力（如内存卸载、CPU offload）对普通用户和资源受限场景至关重要。这次提交本质上是修复了优化机制间的"内耗"，让两种策略可以**叠加**而非**互斥**使用。随着社区模型尺寸持续增长（如视频生成、大分辨率图像模型），内存高效推理会成为核心需求。该提交为复杂内存管理场景奠定了更稳健的基础，并开放了策略定制入口，属于基础设施层面的扎实改进。

## 详细提交记录

### [cae82a7](https://github.com/huggingface/diffusers/commit/cae82a76925be058790096068ea43dcc28075f02)

- **作者**: YiYi Xu
- **时间**: 2026-08-02T21:28:38Z
- **提交信息**: support group offloading under auto offloading (#14358)

Let group offloaded models take part in auto offloading

`ComponentsManager.enable_auto_cpu_offload` and `enable_group_offload` are two
independent hook systems — accelerate's `_hf_hook` and diffusers' `HookRegistry`
— and neither noticed the other. Enabling both raised nothing and appeared to
work, but auto offloading frees memory by calling `.to()`, which a group
offloaded module refuses and only warns about. Every offload the manager thought
it performed was a no-op: it recorded memory as freed that never was, and it
charged a group offloaded model's whole weight against the device although only
one group is ever resident.

A group offloaded model now takes part but places itself. It still makes room by
moving other models aside, since its `pre_forward` consults the strategy as
before; it is never chosen as the thing to move, because moving it does nothing;
and the manager no longer pretends to offload it. Either order works, group
offload before or after enabling.

Deciding *what* to move then has to come from somewhere other than memory
estimates, so `enable_auto_cpu_offload` takes an `offload_strategy` and
`set_offload_strategy` can replace it later. The default `AutoOffloadStrategy`
sizes its decisions from model memory footprints, which do not describe a model
holding one group at a time, so it warns when it meets group offloading — only
when no strategy was passed.

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 428
- **最后更新**: 2026-07-31T09:46:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12791
- **最后更新**: 2026-08-01T19:19:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31098
- **最后更新**: 2026-08-02T21:56:13Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 9
- **主要提交者**: Sugar920, Tao Li, Mick

## AI分析总结

### 综合分析：sgl-project/sglang 昨日提交（第 1/1 批）

#### 一、主要更新类型

- **新功能支持**：BCG（Batch/Chunked Generation）在 MegaMoE 与 FlashInfer A2A 后端上的启用；DCP（Distributed CheckPoint）与 HiCache L2 支持；Diffusion 模型新增 minimax-h3；支持 `return_hidden_states="last"`。
- **Bug 修复**：DSV4 NVFP4 混合加载问题；Rust 服务器 TCP 层 TTFT 停顿修复的回退（Revert）；CI 测试固件过期清理。
- **性能优化 / 后端适配**：AMD gfx950 上 DeepSeek-V4 Fused-RMS FP8 缩放元数据修正；NPU 上自动选择 ascend_attn；benchmark 确定性改进。
- **CI/测试改进**：NPU 新增 PR 测试用例；为 speculative_draft_attention_backend 增加页面约束测试；kv_canary 和 EAGLE 测试夹具的优雅拆除。
- **无文档更新**，以代码与测试为主。

#### 二、关键变更点及其与项目整体方向的关系

1. **BCG 扩展到 MegaMoE 与 FlashInfer A2A 后端**（`8cc941a`）
   - 将此前已部署的批处理/分块生成能力从标准 MoE 推广到更大规模的 MegaMoE 及 FlashInfer A2A 后端。
   - 与项目“高效服务超大规模 MoE 模型”的目标一致，增强多后端兼容性。

2. **DCP + HiCache L2 支持（从 Kimi-K3 移植）**（`1a3bea7`）
   - 引入分布式检查点（DCP）与二级缓存（HiCache L2）能力，为断点续训/推理、分层缓存管理奠定基础。
   - 符合项目在高性能推理系统中提升资源复用与可恢复性的方向。

3. **Diffusion 模型支持 minimax-h3**（`70fe2e0`）
   - 扩大模型覆盖范围，从 LLM 拓展至多模态/Diffusion 领域，增强框架通用性。

4. **支持 `return_hidden_states="last"`**（`a0b7bcf`）
   - 为需要取最后一层隐藏状态的下游任务（如嵌入、分析）提供便捷接口，提升可用性。

5. **Revert "[rust-server] fix TCP-layer TTFT stalls"**（`0655451`）
   - 回退一个旨在降低首个 token 延迟的修复，可能因引入新问题或性能回归而撤回，需要后续重新评估网络层优化策略。

6. **AMD / NPU 后端专项优化**（`1685d29`、`43be25b`、`11d1063c`）
   - 修正 gfx950 FP8 缩放元数据、NPU ascend_attn 自动选择、增加 NPU 测试。体现项目对多硬件平台的重视，降低特定芯片使用门槛。

7. **Benchmark 与 CI 基础设施改进**（`558c9bd`、`0877a0e`、`27b1534`、`43be25b`）
   - 提高测试可重复性、修复过时固件、扩展测试覆盖，确保项目长期稳定发展。

#### 三、对项目的影响和潜在意义

- **模型与服务能力拓宽**：新增 Diffusion 模型与隐藏状态输出接口，使 SGLang 不再局限于纯文本大模型，向多模态和通用推理框架演进。
- **后端生态深化**：BCG 在 MegaMoE 和 FlashInfer A2A 的落地，以及 AMD/NPU 专项优化，表明项目正在巩固其在多供应商硬件上的竞争力，有利于吸引更多生产环境用户。
- **基础设施稳健性**：一系列 CI/测试修补减少了测试波动，提升了开发迭代可靠性；回退有风险修复显示了谨慎的质量控制态度。
- **缓存与检查点能力升级**：DCP + HiCache L2 若平稳落地，将增强框架的工程化水平，支撑大规模分布式服务场景。

#### 四、值得关注的技术点

- **FlashInfer A2A 后端**与 BCG 的组合，可能直接影响 MoE 模型批量推理的吞吐上限。
- **NVFP4 混合精度加载修复**（`ec741e4`）涉及 DeepSeek-V3.2/V4 系列格式，对忠实复现权重重建至关重要。
- **gfx950 FP8 缩放元数据**问题提示我们，不同 GPU 架构对 FP8 格式的元数据解释可能不一致，跨平台部署需注意。
- **Revert 的原因**值得追踪后续提交，网络层 TTFT 优化可能需要更全面的条件判断或回归测试。
- **HiCache L2** 的实现细节（如何与现有 KV cache 结合）可能成为后续性能调优的关键路径。

#### 五、结合 README 背景，这些提交如何影响项目发展

- SGLang 定位为“高性能、低延迟的 LLM 推理与服务框架”，这些提交从 **后端适配、模型覆盖、运行稳定性** 三个维度巩固了这一目标。
- README 展示的活跃开发（高频提交、多协作者）与本次提交内容一致，特别是通过与 Claude 等外部工具协作，加快了功能移植（如

## 详细提交记录

### [8cc941a](https://github.com/sgl-project/sglang/commit/8cc941a672db771c67100afdf1219fa6956a82c7)

- **作者**: Yuwei An
- **时间**: 2026-08-02T21:56:03Z
- **提交信息**: [BCG][4/N] Enable bcg on megamoe & flashinfer a2a backend (#33150)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [ec741e4](https://github.com/sgl-project/sglang/commit/ec741e4161b8c25b575a36f87b781c3d35ededc9)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-02T18:05:09Z
- **提交信息**: Fix DSpark loading for hybrid DSV4 NVFP4 (#33276)

### [1a3bea7](https://github.com/sgl-project/sglang/commit/1a3bea77f2abadb2206ba93293ee4fc4da76742a)

- **作者**: Yuwei An
- **时间**: 2026-08-02T15:35:27Z
- **提交信息**: [Feat] DCP + HiCache L2 Support (ported from kimi-k3) (#33112)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [f8e62a9](https://github.com/sgl-project/sglang/commit/f8e62a9224815cc9c6fc56b940eb7fde791a8870)

- **作者**: Sugar920
- **时间**: 2026-08-02T15:00:02Z
- **提交信息**: [NPU] Add PR test cases (#32392)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [27b1534](https://github.com/sgl-project/sglang/commit/27b15349e5ec6cc452545d2e1836aeeb06dc5bf3)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-02T14:38:45Z
- **提交信息**: [CI] Fix stale CPU test fixtures (#33277)

### [70fe2e0](https://github.com/sgl-project/sglang/commit/70fe2e0dd5e69a062fb146d0db35c7ac939f111f)

- **作者**: Mick
- **时间**: 2026-08-02T14:32:37Z
- **提交信息**: [diffusion] model: support minimax-h3 (#33275)

Co-authored-by: zhenaozhenfu <zhenaozhenfu@minimaxi.com>
Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Zijie Xia <zijie_xia@icloud.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: chao-xue <877184285@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0877a0e](https://github.com/sgl-project/sglang/commit/0877a0e2f1bdc4c0214a025dac60577299703470)

- **作者**: Alison Shao
- **时间**: 2026-08-02T11:58:59Z
- **提交信息**: [CI] Add speculative_draft_attention_backend to the page-constraint test view (#33254)

### [558c9bd](https://github.com/sgl-project/sglang/commit/558c9bdcc2edd4e1fe9345165acc62c885b02f10)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-02T08:39:50Z
- **提交信息**: [misc] Improve benchmark determinism and dataset API coverage (#33255)

### [0655451](https://github.com/sgl-project/sglang/commit/06554515f43e717eb459bb771722d30d80b28298)

- **作者**: Kan Wu
- **时间**: 2026-08-02T08:20:11Z
- **提交信息**: Revert "[rust-server] fix TCP-layer TTFT stalls" (#33257)

### [43be25b](https://github.com/sgl-project/sglang/commit/43be25b2b7121fafd7f1a4f3a7560484ade9f833)

- **作者**: Alison Shao
- **时间**: 2026-08-02T08:09:59Z
- **提交信息**: [CI] Graceful teardown for kv_canary and EAGLE spec fixtures (#32829)

### [8d106c3](https://github.com/sgl-project/sglang/commit/8d106c3d79ef885f2fc0684f1915ebc404acfbe8)

- **作者**: Tao Li
- **时间**: 2026-08-02T07:09:51Z
- **提交信息**: [NPU] Enable automatic ascend_attn selection for vision attention and graph runners (#31948)

Co-authored-by: litao.dream <litao.dream@bytedance.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [a0b7bcf](https://github.com/sgl-project/sglang/commit/a0b7bcf59289a6cf916fa5ee44e3cfa865a25f3d)

- **作者**: Tao Li
- **时间**: 2026-08-02T07:09:33Z
- **提交信息**: [Feature] Support return_hidden_states="last" (#30177)

Co-authored-by: litao.dream <litao.dream@bytedance.com>

### [1685d29](https://github.com/sgl-project/sglang/commit/1685d29f21279349907d8ebbb417a7c339af07a8)

- **作者**: sonle5
- **时间**: 2026-08-02T07:06:09Z
- **提交信息**: [AMD] Fix DeepSeek-V4 fused-RMS FP8 scale metadata on gfx950 (#31727)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1241
- **最后更新**: 2026-08-02T09:32:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 87967
- **最后更新**: 2026-08-02T22:10:41Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: chun-wan, Taneem Ibrahim, Itay Alroy

## AI分析总结

### 主要更新类型

- **Bug修复**：共 2 项（ROCm 精度问题、Elastic EP 权重传输）
- **功能新增/验证**：共 2

## 详细提交记录

### [0033211](https://github.com/vllm-project/vllm/commit/0033211c0bcf3d42d3b1f27059922c30e664b8e7)

- **作者**: chun-wan
- **时间**: 2026-08-02T22:02:42Z
- **提交信息**: [Test][V1] Add sleep/wake correctness regression test for hybrid GDN/… (#44972)

Signed-off-by: chun-wan <chun-wan@amd.com>

### [0055b8b](https://github.com/vllm-project/vllm/commit/0055b8bfa3a2c7c49c51ff5962c162ba85f6de38)

- **作者**: Jason Li
- **时间**: 2026-08-02T20:46:55Z
- **提交信息**: [Attention][MiniMax-M3] Add MSA speculative decode verification (#50032)

### [c666810](https://github.com/vllm-project/vllm/commit/c6668106760e1f8222abd19a6ee9e93fc060cb19)

- **作者**: Fangzhou Ai
- **时间**: 2026-08-02T20:30:54Z
- **提交信息**: [ROCm][Bugfix][Kimi-K3] Preserve MoE correction bias in FP32 (#50761)

Signed-off-by: Fangzhou Ai <Fangzhou.Ai@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [55c98e3](https://github.com/vllm-project/vllm/commit/55c98e370aa058f567a9e682dc0652bdfba6b0bb)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-02T16:46:03Z
- **提交信息**: [Model Runner v2] Enable BGE M3 pooling embed token_classify (#50661)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [96add73](https://github.com/vllm-project/vllm/commit/96add737ff022430b17034ce50dc55504c04094f)

- **作者**: Itay Alroy
- **时间**: 2026-08-02T15:13:42Z
- **提交信息**: [Elastic EP] Fix non-contiguous weight transfers (#50641)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-03
**监控日期**: 2026-08-02
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5796
- **最后更新**: 2026-08-02T21:28:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---
