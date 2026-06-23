# GitHub Stars 合并报告 - 2026-06-23

**合并日期**: 2026-06-24
**监控日期**: 2026-06-23
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


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2041
- **最后更新**: 2026-06-23T18:07:57Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: JimmyMrr, zhangxin.zzzzz

## AI分析总结

**昨日更新要点分析**

---

### 1. 主要更新类型
- **功能新增**：两项提交均为新模型支持，属于功能扩展。

---

### 2. 关键变更点与项目方向关系
- **支持 DeepSeek V4**（`#840`）：深度求索的最新大型语言模型，VeOmni 将其纳入训练框架，表明项目持续跟进前沿大语言模型架构，扩大模型覆盖范围。
- **添加 LTX-2.3 源代码**（`#858`）：LTX 系列为视频/图像生成模型，VeOmni 集成其源码，直接契合项目“任意模态模型训练”的核心目标，拓展了视觉生成领域的支持。

两者均指向 **模型覆盖面扩展**，与项目 README 中 “Scaling Any Modality Model” 的定位一致。

---

### 3. 对项目的影响和潜在意义
- **生态吸引力**：支持热门模型（DeepSeek V4）能吸引更多用户使用 VeOmni 进行训练，增强社区影响力。
- **多模态能力增强**：LTX-2.3 的加入补全了视频生成模态，使平台不仅限于 纯文本/图像，降低用户使用特权代码的迁移成本。
- **技术验证**：集成不同架构模型（LLM + 视觉生成）证明 VeOmni 的分布式训练框架具有较好的通用性，可在统一配方下调度多种模型。

---

### 4. 值得关注的技术点
- **源码集成方式**：LTX-2.3 采用“添加源代码”而非纯配置适配，可能涉及对模型前向/后向的定制优化，值得关注其分布式训练适配细节。
- **DeepSeek V4 支持中的 CI 标签**：提交包含 CI 集成，说明模型支持经过自动化测试，保证了稳定性。

---

### 5. 对项目发展的影响（结合 README）
VeOmni 定位于“模型中心（model-centric）的分布式配方动物园”，每次新增模型支持都相当于在动物园中添置新“物种”。这两条提交：
- 直接兑现了“任意模态”承诺，尤其是 LTX-2.3 确认了视觉生成模型的加入。
- 提升了项目的实用价值：用户无需自己实现分布式训练配置，直接使用预设配方即可训练 DeepSeek V4 或 LTX-2.3。
- 强化了项目作为统一训练框架的角色，有助于构建多模态模型训练的标准生态。

## 详细提交记录

### [880cb87](https://github.com/ByteDance-Seed/VeOmni/commit/880cb8795c74ea086580f86943ebb611c51ac567)

- **作者**: zhangxin.zzzzz
- **时间**: 2026-06-23T18:07:51Z
- **提交信息**: [model, ci] feat: support deepseek v4 (#840)

### [4c45238](https://github.com/ByteDance-Seed/VeOmni/commit/4c45238d20b3b8d08521bc1cf2e876156009d234)

- **作者**: JimmyMrr
- **时间**: 2026-06-23T09:21:08Z
- **提交信息**: [model] feat: add LTX-2.3 source code (#858)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2434
- **最后更新**: 2026-06-23T12:18:38Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Shiqiao Gu (谷石桥)

## AI分析总结

根据你提供的仓库背景和提交记录，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：支持 FP8 精度的 infinitetalk 模型推理（#1177）
- **配置更新**：更新了相关配置文件（#1179），属于功能配套的配置调整

### 2. 关键变更点与项目方向的关系
- **关键变更**：引入 FP8 量化推理能力，并适配 infinitetalk 模型（一种可能面向长视频或对话式视频生成的模型）。
- **与项目方向的关系**：项目 LightX2V 定位为“轻量视频生成推理框架”，FP8 支持直接降低显存占用和计算延迟，符合“轻量”核心目标；同时扩展支持的模型类型（infinitetalk），增强框架的通用性和覆盖面。

### 3. 对项目的影响和潜在意义
- **性能提升**：FP8 推理可显著减少显存需求、提升推理吞吐量，尤其适合资源受限环境（如边缘设备或低成本云实例）。
- **模型生态扩展**：infinitetalk 模型可为长视频生成或交互式视频生成场景提供新能力，拓宽框架的应用场景（如短视频生成、实时对话式视频等）。
- **配置标准化**：配置更新反映了对模型参数、推理流程的持续优化，有助于用户快速适配新模型。

### 4. 值得关注的技术点
- **FP8 量化推理**：需要考察 FP8 精度是否影响生成质量，以及底层实现（如是否使用 NVIDIA Transformer Engine 或自定义量化 kernel）。
- **Infinitetalk 模型架构**：可能涉及长序列视频生成、自回归或扩散模型变体，其 FP8 适配的稳定性值得关注。
- **配置文件的改动范围**：可能与模型路径、精度开关、采样参数等有关，影响用户的使用方式。

### 5. 对项目发展的影响
- **强化轻量优势**：FP8 支持进一步巩固了 LightX2V 在高效推理方面的竞争力，与其他视频生成框架（如 DiffSynth 等）形成差异。
- **加速新模型集成**：infinitetalk 的引入表明框架具备快速适配新模型的能力，有利于吸引社区贡献更多模型。
- **降低使用门槛**：用户无需高显存显卡即可运行更复杂的视频生成模型（如长视频），扩大潜在用户群体。

需要进一步深入分析时，可查看具体配置文件和 FP8 实现的代码细节。

## 详细提交记录

### [62c0204](https://github.com/ModelTC/LightX2V/commit/62c0204aa433096510788e0c368054e28bb43dda)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-06-23T11:15:01Z
- **提交信息**: update configs (#1179)

### [202f916](https://github.com/ModelTC/LightX2V/commit/202f9164d1721e07277fb3a22a188b4cf60048c9)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-06-23T09:11:55Z
- **提交信息**: support fp8 infinitetalk models (#1177)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2145
- **最后更新**: 2026-06-23T12:35:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5844
- **最后更新**: 2026-06-23T21:12:23Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yue Weng, Duncan Moss

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **Bug修复（2项）**：全部为修复性提交，无新增功能或性能优化。

#### 2. 关键变更点及其与项目整体方向的关系
| 提交 | 关键变更 | 与项目方向的关系 |
|------|----------|------------------|
| `0b727e6` | 修复 tinygemm 中的 barrier 同步 bug（与 TensorRT-LLM 集成相关） | tinygemm 是实现低精度矩阵乘法的核心 kernel，直接影响推理速度和正确性；barrier 错误可能导致死锁或数据竞争，修复后确保高并发时稳定执行。 |
| `5197858` | 修复 top-p（nucleus）采样算法中，当候选概率边界为相邻 FP32 值时搜索无法终止的问题 | top-p 采样是生成式推理的关键解码策略；错误收敛条件会导致采样结果异常或性能退化，修复后增强数值稳定性，使采样逻辑在极端浮点边界下仍能正确结束。 |

#### 3. 对项目的影响和潜在意义
- **可靠性提升**：两项修复都消除了可能导致程序崩溃或结果错误的潜在缺陷，尤其 tinygemm bug 来自外部社区报告（TensorRT-LLM #15338），对依赖 FlashInfer 的推理框架（如 vLLM、TensorRT-LLM）至关重要。
- **用户信心**：修复了社区发现的问题，体现了项目对正确性的重视，有利于吸引更多用户在生产环境中部署。
- **维护性**：top-p 搜索的改进明确了浮点数收敛的数学边界，未来修改不易引入同类问题。

#### 4. 值得关注的技术点
- **Barrier 同步**：在 GPU kernel 中使用 barrier 实现线程间同步是 CUDA 编程的经典难题，此修复可能涉及 `__syncthreads` 与 warp 级别同步之间的协调，值得开发者学习。
- **浮点数收敛判别**：top-p 搜索采用三元搜索（ternary search），当上下界为相邻可表示 FP32 值时，继续二分搜索无法产生新值，必须提前终止。这一小技巧在数值算法中常被忽略，但却是保证循环收敛的关键。

#### 5. 基于项目背景对项目发展的影响
FlashInfer 定位为 **“用于推理的高性能 GPU Kernel 库”**，其核心价值在于稳定、正确且高效地支撑各种推理场景。这两项修复：
- **强化核心推理流水线**：tinygemm 影响注意力机制中的 Q、K、V 投影计算，top-p 影响生成阶段的采样逻辑，两者都是推理中的高频环节。
- **减少生产事故隐患**：推理框架通常将 FlashInfer 作为依赖库使用，任何未修复的 bug 都可能在上层框架中放大。及时修复提升了 FlashInfer 作为底层库的成熟度。
- **推动与主流框架的兼容性**：tinygemm bug 与 TensorRT-LLM 紧密相关，修复后 FlashInfer 与 TensorRT-LLM 的集成更加可靠，有利于形成更广泛的社区生态。

## 详细提交记录

### [0b727e6](https://github.com/flashinfer-ai/flashinfer/commit/0b727e676ad0d7504000813601d2ef88ae4881c7)

- **作者**: Yue Weng
- **时间**: 2026-06-23T16:51:14Z
- **提交信息**: fix: fix tinygemm barrier bug (#3630)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix tinygemm barrier bug. Update the integration in FlashInfer. More
details in https://github.com/NVIDIA/TensorRT-LLM/pull/15338

Thanks to @LorrinWWW for reporting this bug and for providing a very
detailed script to reproduce it.

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

* **Refactor**
* Optimized GPU kernel synchronization mechanism for improved compute
thread efficiency in barrier polling operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5197858](https://github.com/flashinfer-ai/flashinfer/commit/5197858b22ed7aa85e4919d11435a4300ffd07c8)

- **作者**: Duncan Moss
- **时间**: 2026-06-23T16:34:03Z
- **提交信息**: fix(sampling): terminate top-p search at adjacent float bounds (#3623)

## Summary

Updates the small-vocab top-p renormalization threshold search to stop
when the remaining candidate bounds are adjacent FP32 values.

## Details

The previous loop required exact equality between the candidate bounds.
Once the bounds are adjacent representable floats, further ternary
refinement may not collapse them to an identical value, so the loop
should treat that interval as converged.

## Validation

- `git diff --check upstream/main..HEAD`
- Focused GPU top-p reference checks for small-vocab scalar and
per-request `top_p`


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved numerical stability in the Top-P probability renormalization
step by refining the floating-point loop termination logic, preventing
incorrect behavior near numerical boundaries where values no longer make
progress due to representation limits.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3744
- **最后更新**: 2026-06-23T21:18:01Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 5
- **主要提交者**: Raghav K, xsank, Loay Rashid

## AI分析总结

### 1. 主要更新类型

- **CI/基础设施优化**：提交1、5、6、8、9
- **Bug修复**：提交7、10、11
- **性能优化**：提交4
- **文档更新**：提交3
- **版本发布**：提交6
- **代码清理**：提交2

### 2. 关键变更点及其与项目整体方向的关系

| 提交 | 变更内容 | 与项目方向的关系 |
|------|----------|------------------|
| 7cebf5f | 限制 kernel wheel 构建并行度，避免 CI Runner OOM | 保证 CI 稳定性，支撑持续集成效率 |
| d303b4e | 更新 README 文档 | 保持项目介绍和快速入门信息最新，方便新用户 |
| 31b719a | 优化 compress & topk 核函数性能 | 直接提升视频生成/训练中关键算子的速度，属于核心性能优化 |
| 887aaf3 | 升级 CUDA Toolkit Action 到 v0.2.35，修复 cu130 发布 | 解决特定 CUDA 版本下的构建问题，保障多环境兼容 |
| b1d89eb | 发布 fastvideo-kernel 0.3.0 | 正式提供优化后的内核组件，推动版本化迭代 |
| 995a5fd | 修复 fastwan 脚本中的去噪时间计算错误 | 修正推理流程中的时间逻辑，保证生成质量 |
| 4d6ac89 | 新增指标回归测试+身份不变性CI测试 | 建立质量门禁，防止性能退化，强化评估体系 |
| 4171cac | 为 Cosmos-Predict2.5 2B 模型接入正确采样预设 | 支持新模型正常推理，扩展模型生态 |
| b2ade71 | 修复 QAD 5090: Torch.compile 和其他优化 | 适配特定硬件（5090）并优化编译，提升部署效率 |
| dd0f4b6 | 清理杂项文件 | 减少冗余，保持仓库整洁 |

### 3. 对项目的影响和潜在意义

- **稳定性提升**：CI OOM 修复和自动化合并策略调整，减少了构建失败和人为干预，加速开发流程。
- **性能跃升**：compress & topk 核函数优化直接降低视频生成/训练中计算瓶颈，预计缩短推理时间，提升每秒帧数。
- **生态扩展**：支持 Cosmos-Predict2.5 新模型，修复去噪时间 bug，增强了框架对不同视频生成架构的兼容性。
- **质量保障**：新增回归测试和身份不变性测试，为后续 PR 提供量化基准，防止无意识退化，对长期维护至关重要。
- **用户友好**：README 更新和版本发布让用户能快速上手并享受优化成果；清理杂项也降低了使用门槛。

### 4. 值得关注的技术点

1. **compress & topk kernel 优化**：这很可能是视频压缩或 Token 选择的计算核心，优化后可能大幅减少显存占用和推理延迟，建议关注具体加速比例。
2. **Torch.compile 优化与 QAD 5090**：针对特定 GPU（RTX 5090）的编译适配，表明项目正积极适配最新硬件特性，提升在消费级 GPU 上的部署体验。
3. **新的 CI 测试**：metric regression（指标回归）和 identity-invariant（身份不变性）测试，前者防止 PSNR/SSIM 等指标下滑，后者验证视频生成内容的一致性，属于高级质量保证手段。
4. **kernel 0.3.0 发布**：标志着内核组件进入稳定阶段，后续可能仅做 bug 修复和微调，降低用户依赖的不确定性。

### 5. 与项目发展方向的关联

- FastVideo 旨在提供高效、易

## 详细提交记录

### [7cebf5f](https://github.com/hao-ai-lab/FastVideo/commit/7cebf5f82cb09fc6b0be65c9a1342035db61f3b4)

- **作者**: William Lin
- **时间**: 2026-06-23T21:17:56Z
- **提交信息**: [ci] cap kernel wheel build parallelism to avoid runner OOM (#1483)

### [dd0f4b6](https://github.com/hao-ai-lab/FastVideo/commit/dd0f4b6753700405c7401cae6bf03d6468ff4dc7)

- **作者**: William Lin
- **时间**: 2026-06-23T21:17:22Z
- **提交信息**: [misc] cleanup misc files (#1484)

### [d303b4e](https://github.com/hao-ai-lab/FastVideo/commit/d303b4e03a260f06293e113ed06bfb3144f8ea8e)

- **作者**: William Lin
- **时间**: 2026-06-23T19:07:21Z
- **提交信息**: [docs] update README (#1482)

### [31b719a](https://github.com/hao-ai-lab/FastVideo/commit/31b719ae491972735f813c8e31a5287fadd534d1)

- **作者**: xsank
- **时间**: 2026-06-23T18:51:22Z
- **提交信息**: [perf] optimize compress & topk kernel (#1421)

Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [887aaf3](https://github.com/hao-ai-lab/FastVideo/commit/887aaf3d3e9bb3fcb2c1684d9a1cafbebdc11c83)

- **作者**: William Lin
- **时间**: 2026-06-23T17:33:31Z
- **提交信息**: [ci] bump cuda-toolkit action to v0.2.35 to fix kernel cu130 publish (#1481)

### [b1d89eb](https://github.com/hao-ai-lab/FastVideo/commit/b1d89eba1f177f2b096192c9b1e7ceb7096bea99)

- **作者**: William Lin
- **时间**: 2026-06-23T17:02:27Z
- **提交信息**: [chore] release fastvideo-kernel 0.3.0 (#1478)

### [995a5fd](https://github.com/hao-ai-lab/FastVideo/commit/995a5fdf977e1db35dbb962b87c1f122fad63d8b)

- **作者**: Loay Rashid
- **时间**: 2026-06-23T17:01:23Z
- **提交信息**: [bugfix] fixing denoising time in the fastwan script (#1480)


Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [70a70b6](https://github.com/hao-ai-lab/FastVideo/commit/70a70b689e55710a17bcb8ef1d87d4f2ac2beb5c)

- **作者**: William Lin
- **时间**: 2026-06-23T10:23:58Z
- **提交信息**: [ci] mergify: stop auto-syncing ready PRs (#1477)

### [4d6ac89](https://github.com/hao-ai-lab/FastVideo/commit/4d6ac89b43929241c84fb05fa48d6f7e577a7d56)

- **作者**: Shao Duan
- **时间**: 2026-06-23T08:27:34Z
- **提交信息**: [ci] eval: add metric regression + identity-invariant ci tests (#1451)

### [4171cac](https://github.com/hao-ai-lab/FastVideo/commit/4171cacd93ce42e17d8055620b240f22dacc78db)

- **作者**: Raghav K
- **时间**: 2026-06-23T08:25:35Z
- **提交信息**: [bugfix] Wire Cosmos-Predict2.5 2B to its sampling preset (#1468)

### [b2ade71](https://github.com/hao-ai-lab/FastVideo/commit/b2ade71467050f448aac74ac77b1794a81ed18cf)

- **作者**: Loay Rashid
- **时间**: 2026-06-23T08:23:57Z
- **提交信息**: [Bugfix] QAD 5090: Torch.compile and other optimizations (15/12) (#1466)

Co-authored-by: alexzms <3036648523@qq.com>
Co-authored-by: Kaiqin Kong <k1kong@ucsd.edu>
Co-authored-by: William Lin <SolitaryThinker@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33908
- **最后更新**: 2026-06-23T17:15:04Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, apolinário

## AI分析总结

根据提供的提交记录和项目背景（HuggingFace Diffusers 扩散模型库），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：修复模型CUDA测试相关问题（提交 `6a71b6e`）
- **功能新增**：添加Krea 2 LoRA DreamBooth训练器及LoRA加载支持（提交 `3993de5`）

### 2. 关键变更点及其与项目整体方向的关系
- **模型CUDA测试修复**：主要涉及将一组模型测试移植到CUDA环境、修复特征提取器中的错误、并回退部分改动后进一步修正。这直接关系到Diffusers库在多平台（特别是GPU）上的测试可靠性，是维护库质量的基础工作。
- **Krea 2 LoRA DreamBooth训练器**：
  - 新增示例脚本 `train_dreambooth_lora_krea2.py`
  - 引入 `Krea2LoraLoaderMixin`，使 `Krea2Pipeline` 支持保存/加载LoRA适配器
  - 修改Transformer/Pipeline前向方法以支持 `attention_kwargs` 参数，实现运行时LoRA缩放
  - 更新文档，将 `Krea2LoraLoaderMixin` 添加到LoRA加载器文档中
  - 这扩展了Diffusers对具体架构（Krea 2）的LoRA微调支持，符合库不断添加新模型和新训练范例的方向。

### 3. 对项目的影响和潜在意义
- **测试修复**：确保CUDA环境下的模型测试通过，避免因GPU相关错误导致用户崩溃，提升库的稳定性和开发者体验。
- **Krea 2 LoRA支持**：
  - 使Krea 2模型用户能够利用LoRA进行高效微调（DreamBooth），降低个人化生成的门槛。
  - 将LoRA加载机制泛化到Krea架构，为未来其他模型集成LoRA提供参考。
  - 新增的训练脚本丰富了示例库，有助于社区快速上手特定模型的DreamBooth微调。

### 4. 值得关注的技术点
- **CUDA测试修复中的回退策略**：开发者先移植了测试集，遇到问题后回退，再逐步修复，体现了谨慎的测试维护方式。
- **LoRA加载器Mixin设计**：`Krea2LoraLoaderMixin` 是混合类，表明Diffusers采用Mixin模式将LoRA加载能力注入特定Pipeline，保持了架构的模块化。
- **运行时LoRA缩放**：通过 `attention_kwargs` 传递缩放参数，允许在不改变权重文件的情况下调整LoRA影响强度，是LoRA部署中的实用功能。

### 5. 基于README背景的项目发展分析
- Diffusers的核心目标是提供一个可扩展、模块化的扩散模型库，支持多种架构、训练方法和推理优化。  
  - **CUDA测试修复**：增强了库对GPU设备的兼容性，是维持多平台可用性的必要保障，符合库“开箱即用”的愿景。  
  - **Krea 2 LoRA DreamBooth支持**：进一步丰富了库支持的模型家族（Krea 2），并强化了LoRA这一轻量级微调方式在库中的地位。这有助于吸引更多模型社区用户，推动库成为扩散模型生态的“标准工具箱”。同时，通过提供示例脚本和文档，降低了用户学习成本，体现了项目对易用性和社区贡献的重视。

## 详细提交记录

### [6a71b6e](https://github.com/huggingface/diffusers/commit/6a71b6e332abae01a05d36133003e5370ca1d0a8)

- **作者**: Sayak Paul
- **时间**: 2026-06-23T12:12:36Z
- **提交信息**: Fix model cuda tests (#13975)

* port final set of model tests and others

* fix extracter.

* fix cuda tests for models.

* Revert "fix extracter."

This reverts commit 178c4cb99be7ca9f28aeee556e37e9436c5e6f66.

* Revert "port final set of model tests and others"

This reverts commit a92c70c08116511e0977c0e71595219d32834f02.

* fix more

* address reviewer feedback

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [3993de5](https://github.com/huggingface/diffusers/commit/3993de59e37344d92aa24ec25bdc39413157b744)

- **作者**: apolinário
- **时间**: 2026-06-23T12:09:27Z
- **提交信息**: Krea 2 LoRA DreamBooth trainer (#14046)

* Add Krea 2 LoRA DreamBooth trainer + Krea2 LoRA loader

Adds examples/dreambooth/train_dreambooth_lora_krea2.py and the
Krea2LoraLoaderMixin (Krea2Pipeline now inherits it) so LoRA adapters
can be saved/loaded for the Krea 2 transformer. The transformer/pipeline
forward now accept attention_kwargs for runtime LoRA scaling.

Co-Authored-By: linoytsaban <linoy.tsaban@gmail.com>

* inline _pack/_unpack_latents in trainer (pipeline methods are instance methods)

* add Krea2LoraLoaderMixin to LoRA loaders docs

* remove mu from validation call to align with pipeline on main

---------

Co-authored-by: linoytsaban <linoy.tsaban@gmail.com>
Co-authored-by: Linoy Tsaban <57615435+linoytsaban@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 417
- **最后更新**: 2026-06-22T04:30:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12615
- **最后更新**: 2026-06-23T16:47:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29567
- **最后更新**: 2026-06-23T22:54:42Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 19
- **主要提交者**: Cheng Wan, Xiaoyu Zhang, ybyang

## AI分析总结

根据昨日（2025-04-10）的 29 条提交记录，结合项目背景（sglang 是一个高性能 LLM 推理框架，支持多种硬件、扩散模型、缓存优化等），总结更新要点如下：

---

### 1. 主要更新类型

| 类型 | 数量 | 典型提交 |
|------|------|----------|
| **性能优化** | 8 | TF32 matmul (#22744)、AMD Triton kernel fuse (#28084)、dsv4 高并发优化 (#28938)、FlashInfer MoE autotune (#29069)、SM90 allreduce 融合 (#28789)、diffusion causal attention fastpath (#28760) 等 |
| **Bug 修复** | 6 | streaming logprobs 修复 (#28601)、HiCache 内存泄漏 (#28916)、SANA VAE dtype 修复 (#28769)、flaky 测试修复 (多笔) |
| **重构/清理** | 5 | ZMQ IPC 封装 (#29012)、bench_one_batch 迁移 (#28687)、废弃 dead buffers (#28968)、统一 spec-v2 KV bookkeeping (#28754) |
| **功能

## 详细提交记录

### [34dd9c2](https://github.com/sgl-project/sglang/commit/34dd9c28caf4f7dd185e58e462a1344b52568e2e)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-23T22:54:36Z
- **提交信息**: [Refactor] Introduce sock_send/sock_recv wrappers for zmq IPC (#29012)

### [ecab3f3](https://github.com/sgl-project/sglang/commit/ecab3f322e5e2b52c929a5aaf962b3bb4b7a8cb4)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-23T22:46:22Z
- **提交信息**: Revert "Improve MFU metrics for prefill and verify timing" (#29079)

### [11e7c9e](https://github.com/sgl-project/sglang/commit/11e7c9e0e6535eefdebafc28bc5bbf0d998a1e16)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-23T21:57:35Z
- **提交信息**: [misc] Add sglang.bench_one_batch deprecation shim (#29082)

### [f74a172](https://github.com/sgl-project/sglang/commit/f74a1722e632b547d77eb9484fc97d4650e1fa8c)

- **作者**: Trevor Morris
- **时间**: 2026-06-23T21:54:54Z
- **提交信息**: [NVIDIA] Support TF32 matmul to improve MiniMax gate gemm performance (#22744)

### [c864c8d](https://github.com/sgl-project/sglang/commit/c864c8d9c25eb1875b91b431640852fa31e613ea)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-23T21:48:35Z
- **提交信息**: [misc] Move bench_one_batch into sglang/benchmark/ with a back-compat shim (#28687)

### [6c5f466](https://github.com/sgl-project/sglang/commit/6c5f4660238dd9d81df603c9e6bfc6122ad97f94)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-23T21:21:59Z
- **提交信息**: [server_args] Reland FA4 page_size auto-force for combined --attention-backend fa4 (#28976)

### [93015a9](https://github.com/sgl-project/sglang/commit/93015a9e6b11e584f4285f71d7779c4855f7d1a8)

- **作者**: YAMY
- **时间**: 2026-06-23T20:31:47Z
- **提交信息**: fix(runner): autotune flashinfer MoE on a decode-shaped buffer (#29069)

### [fc27ce0](https://github.com/sgl-project/sglang/commit/fc27ce06660fc0641e9103696360bf1dd28b852f)

- **作者**: Jan Bernlöhr
- **时间**: 2026-06-23T20:30:51Z
- **提交信息**: Add GB10 FP8 fused MoE Triton config (#25665)

### [cedb43d](https://github.com/sgl-project/sglang/commit/cedb43d5229bf1e335255076ba9eec325705c8b6)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-23T20:19:47Z
- **提交信息**: [DeepEP] Gate DeepEP MNNVL on fabric support (#28942)

### [b60185c](https://github.com/sgl-project/sglang/commit/b60185c41cb0cbd3d1f09866023c04bd85bedf37)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-23T19:26:56Z
- **提交信息**: Improve MFU metrics for prefill and verify timing (#29000)

Co-authored-by: Pranjal Shankhdhar <pranjal.ssh@gmail.com>

### [0c6e8e9](https://github.com/sgl-project/sglang/commit/0c6e8e94773b751773365f15ef69267f85e1f813)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-23T19:26:37Z
- **提交信息**: Expand parser auto detection coverage (#28449)

### [e0dc8b7](https://github.com/sgl-project/sglang/commit/e0dc8b7137dfee6fe168fc8210961970588a2e5a)

- **作者**: karverma-amd
- **时间**: 2026-06-23T18:15:12Z
- **提交信息**: [AMD] Fuse topk padded-token masking into a single Triton kernel (#28084)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [ed26a10](https://github.com/sgl-project/sglang/commit/ed26a109eeed967e3a43e8f6bef5b6ec30484cf0)

- **作者**: Khoa Pham
- **时间**: 2026-06-23T16:56:09Z
- **提交信息**: [Fix] Return streaming logprobs when reasoning/tool parser is active (#28601)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [83d32fb](https://github.com/sgl-project/sglang/commit/83d32fbc2f2a8fdb5a7bec20f0470191fff5a1dc)

- **作者**: Yihao Wang
- **时间**: 2026-06-23T16:26:51Z
- **提交信息**: remove lora section (#29056)

### [b5e0965](https://github.com/sgl-project/sglang/commit/b5e0965b07a221f38fc576b87b79c101316b1aae)

- **作者**: Yihao Wang
- **时间**: 2026-06-23T15:02:08Z
- **提交信息**: [Diffusion][Cookbook] Add Krea-2 cookbook (#29051)

### [31d71c4](https://github.com/sgl-project/sglang/commit/31d71c47afda6043e44ba923b6897af698fd8889)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-23T14:57:08Z
- **提交信息**: [Diffusion] Fix SANA VAE dtype and TurboWan backend selection (#28769)

### [12b08e6](https://github.com/sgl-project/sglang/commit/12b08e620b6d509d13c6d7456230c36359657954)

- **作者**: Thomas
- **时间**: 2026-06-23T14:25:10Z
- **提交信息**: [Diffusion] [NPU] enable Helios on npu (#29011)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [c67d338](https://github.com/sgl-project/sglang/commit/c67d338637f2574fcf66f64b233557c15f8b310c)

- **作者**: Thomas
- **时间**: 2026-06-23T13:08:03Z
- **提交信息**: [Diffusion] enable cache-dit for ERNIE-Image model (#28266)

### [0460f27](https://github.com/sgl-project/sglang/commit/0460f277b770f8b5a404da2e50e7a9573ef8db40)

- **作者**: Shangming Cai
- **时间**: 2026-06-23T09:52:26Z
- **提交信息**: Fix manual chunked-prefill test to use req.fill_len after fill_ids refactor (#29032)

### [ed0a62e](https://github.com/sgl-project/sglang/commit/ed0a62e4dd006132a2c6434378962528f010c906)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-23T09:29:40Z
- **提交信息**: [Mem] Add KV-page double-free checks to the invariant checker (#27731)

### [af9027f](https://github.com/sgl-project/sglang/commit/af9027f6c938b07995e507ac78496ceef3014d31)

- **作者**: kk
- **时间**: 2026-06-23T09:20:48Z
- **提交信息**: [AMD] Improve performance of dsv4 in high concurrency (#28938)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [a65c68c](https://github.com/sgl-project/sglang/commit/a65c68c1fb92ebfeb01c2cbfed3c9fc34fcf7386)

- **作者**: Shangming Cai
- **时间**: 2026-06-23T08:53:32Z
- **提交信息**: Revert "[CI] Fix flaky optimistic test by adding contention handling" (#29023)

### [e67b228](https://github.com/sgl-project/sglang/commit/e67b228d4c03fb92014fba6bd7d20b6392ae2db4)

- **作者**: ishandhanani
- **时间**: 2026-06-23T08:51:41Z
- **提交信息**: feat: session radix cache (#27058)

Signed-off-by: Ishan Dhanani <ishandhanani@gmail.com>

### [349a6af](https://github.com/sgl-project/sglang/commit/349a6af6b8c57b7a579828f842348030ea6e19b6)

- **作者**: ybyang
- **时间**: 2026-06-23T08:39:03Z
- **提交信息**: [HiCache] Fix hicache host memory leak by bounding PP-sync work_list (#28916)

### [7b1a203](https://github.com/sgl-project/sglang/commit/7b1a20344c842a522b30b49f3cd6b198866f830f)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-23T08:29:19Z
- **提交信息**: Re-enable SM90 FlashInfer allreduce fusion with safe backend defaults (#28789)

### [854c688](https://github.com/sgl-project/sglang/commit/854c688121ed29f49bc862fe19357eecd6c72b30)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-23T07:53:05Z
- **提交信息**: [Spec] Unify decode KV-commit bookkeeping across spec-v2 workers (#28754)

### [743ce88](https://github.com/sgl-project/sglang/commit/743ce88bc5f5bf02a84a7f07926f3b6a9aecbd3d)

- **作者**: cctry
- **时间**: 2026-06-23T07:18:01Z
- **提交信息**: Fix flaky optimistic prefill retry test (#28995)

Co-authored-by: cctry <cctry@fb.com>

### [219742c](https://github.com/sgl-project/sglang/commit/219742c3948e70b3a4e2e7563dc59fcf13ff5a90)

- **作者**: Mick
- **时间**: 2026-06-23T07:15:30Z
- **提交信息**: [diffusion] optimize: optimize realtime causal attention fastpath (#28760)

### [c4376aa](https://github.com/sgl-project/sglang/commit/c4376aaa887af614dae01939fc2c896a32d490da)

- **作者**: Cheng Wan
- **时间**: 2026-06-23T07:03:30Z
- **提交信息**: [Refactor] Remove dead out_cache_loc_swa buffers (#28968)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1208
- **最后更新**: 2026-06-23T12:39:16Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

### 昨日更新总结

#### 1. 主要更新类型
- **功能新增**：CLI（命令行界面）支持传递额外输入关键字参数（extra input kwargs）。

#### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：CLI命令现在可以接受用户自定义的额外参数（通过 `kwargs`），并传递给底层推理引擎。
- **与项目方向的关系**：`cache-dit` 作为一个以易用性为目标的 PyTorch 原生推理引擎（支持缓存、并行、量化、CPU Offload），CLI 是用户快速体验和集成该引擎的关键入口。支持额外参数扩展了 CLI 的灵活性和可配置性，允许用户通过命令行直接控制引擎的各类高级选项（如缓存策略、量化精度等），而无需修改 Python 代码，这符合项目“降低使用门槛”的定位。

#### 3. 对项目的影响和潜在意义
- **提升可用性**：用户可以通过命令行脚本更灵活地试验不同配置（例如指定不同 DiT 模型、调整推理参数），便于快速原型验证和自动化部署。
- **增强生态集成**：`kwargs` 机制使得 CLI 能够适应未来新增的引擎参数（如新的量化方法或缓存模式），无需频繁修改 CLI 代码，降低了维护成本。
- **潜在意义**：吸引更多非深度 Python 用户（如 DevOps、MLOps 工程师）使用 `cache-dit`，促进项目社区成长。

#### 4. 值得关注的技术点
- **CLI 参数解析设计**：如何安全、高效地将 `kwargs` 从命令行字符串转换为 Python 字典，并传递给底层函数；可能需要处理类型转换、默认值覆盖和错误校验。
- **兼容性**：确保 `kwargs` 不会与已有的 CLI 参数冲突，且能够正确传递给 DiT 推理的 `forward` 方法或引擎初始化函数。

#### 5. 基于项目背景的本提交对项目发展的影响
- **推动 CLI 成熟化**：从“基础CLI”向“可扩展CLI”演进，为后续支持更多复杂场景（如批量推理、分布式命令）奠定基础。
- **强化“推理引擎”定位**：通过 CLI 直接暴露引擎核心能力（如 `--cache_strategy`、`--quantize` 等潜在参数），使用户无需阅读文档或编写代码即可体验 `cache-dit` 的性能优势，加速项目在扩散模型推理领域的采纳。
- **对齐 README 目标**：README 强调“易用性”和“原生”，本次更新直接提升了命令行交互的易用性。

## 详细提交记录

### [4d8f973](https://github.com/vipshop/cache-dit/commit/4d8f973f731d1a25eb027c3b336fbdaac0aee791)

- **作者**: DefTruth
- **时间**: 2026-06-23T09:18:20Z
- **提交信息**: CLI: support extra input kwargs (#1068)

* CLI: support extra input kwargs

* CLI: support extra input kwargs

* CLI: support extra input kwargs

* CLI: support extra input kwargs

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 83654
- **最后更新**: 2026-06-23T23:33:26Z

## 提交统计

- **昨日提交总数**: 51
- **提交者数量**: 40
- **主要提交者**: Guy Stone, Gabriel Wu, Rui Yin

## AI分析总结

分析生成失败

## 详细提交记录

### [d86c66c](https://github.com/vllm-project/vllm/commit/d86c66c981006b2e7f6eef3b32145a4ddc67425a)

- **作者**: Roberto L. Castro
- **时间**: 2026-06-23T23:33:17Z
- **提交信息**: [Feat] Add runtime monitor for post-warmup CuTeDSL compilation (#46167)

### [80e5117](https://github.com/vllm-project/vllm/commit/80e511772f3e83461fc3f73112b0ee1664713cde)

- **作者**: Nico Holmberg
- **时间**: 2026-06-23T23:19:51Z
- **提交信息**: [ROCm][Bugfix][Perf] enable shared expert fusion for Qwen3.5 (#44434)

Signed-off-by: Nico Holmberg <nico.holmberg@amd.com>

### [855cd4d](https://github.com/vllm-project/vllm/commit/855cd4d787608b9bdecdc491d51fefadd3fc67dd)

- **作者**: Roberto L. Castro
- **时间**: 2026-06-23T23:11:00Z
- **提交信息**: [Perf][DSv4/DSv3.2] Add cluster-cooperative topK kernel for low-latency scenarios (#43008)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>

### [3cc871a](https://github.com/vllm-project/vllm/commit/3cc871aaf1554dfaebce86a6798965ec47e708da)

- **作者**: Guy Stone
- **时间**: 2026-06-23T22:46:09Z
- **提交信息**: [Perf] Skip detokenization in online beam search (#46422)

Signed-off-by: Guy Stone <guys@spotify.com>
Signed-off-by: Guy Stone <guystone3@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0a3e2db](https://github.com/vllm-project/vllm/commit/0a3e2dbc09c8a70dfd18f728bb829bf29ffa7da6)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-23T21:54:46Z
- **提交信息**: [Optimization] Skip DP padding tokens in MoE (#46428)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [84f1337](https://github.com/vllm-project/vllm/commit/84f13374b350fba78872f8612c3a839256815a4a)

- **作者**: fxmarty-amd
- **时间**: 2026-06-23T21:38:06Z
- **提交信息**: [CI] Fix `test_auto_gptq` on ROCm CI (#46164)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b28103e](https://github.com/vllm-project/vllm/commit/b28103e1ca8b697db917c9572bb0ba6e270c6c20)

- **作者**: Micah Williamson
- **时间**: 2026-06-23T21:32:05Z
- **提交信息**: [ROCm][CI] Shard LM Eval Qwen3-5 Models (B200-MI355) in AMD CI (#46520)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [abc3313](https://github.com/vllm-project/vllm/commit/abc33134fa773690f6c89121baa119626a374c3e)

- **作者**: Wentao Ye
- **时间**: 2026-06-23T21:01:34Z
- **提交信息**: [CI Test] Mark batch invariance test flaky (#46530)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [6617db1](https://github.com/vllm-project/vllm/commit/6617db1bfba34fce90e56f8876db1490ca530bc5)

- **作者**: Maxwill Lin
- **时间**: 2026-06-23T20:43:11Z
- **提交信息**: [Bugfix][Frontend] Emit non-ASCII tool-call arguments without \uXXXX escapes (#46308)

Signed-off-by: EazyReal <8047065+EazyReal@users.noreply.github.com>
Co-authored-by: EazyReal <8047065+EazyReal@users.noreply.github.com>

### [899d72a](https://github.com/vllm-project/vllm/commit/899d72a58c118035be5e9420a15cfa1110c64f47)

- **作者**: Ting SUN
- **时间**: 2026-06-23T20:29:34Z
- **提交信息**: [Bugfix][ToolParser] Handle braces in required tool streaming strings (#45389)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [11b56b2](https://github.com/vllm-project/vllm/commit/11b56b2ff28eae32a1e65c051c24b50f3c39e03d)

- **作者**: Yongye Zhu
- **时间**: 2026-06-23T19:45:49Z
- **提交信息**: [Kernel] Add FlashInferCutedslMxfp8LinearKernel (cute-dsl mm_mxfp8) (#46393)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>

### [0d4d164](https://github.com/vllm-project/vllm/commit/0d4d164488cb29bdc9fbfe3cd943da4b854ae19c)

- **作者**: Gabriel Wu
- **时间**: 2026-06-23T19:43:36Z
- **提交信息**: [Bugfix] Allow flashinfer_cutlass as a clamped NVFP4 MoE backend (#46492)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Signed-off-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [0775b88](https://github.com/vllm-project/vllm/commit/0775b882ba22572f851a439a705ef42b156051d8)

- **作者**: Mike G
- **时间**: 2026-06-23T19:21:19Z
- **提交信息**: [NVFP4 MoE/Deepseek V4] Marlin: wire SwiGLU clamp + allow it for clamped models on non-Blackwell (#45836)

Signed-off-by: Mike G <180722391+mikekg@users.noreply.github.com>

### [7c2e084](https://github.com/vllm-project/vllm/commit/7c2e08451a474972ce5a409b88d937f9cc08a243)

- **作者**: Michael Goin
- **时间**: 2026-06-23T19:16:51Z
- **提交信息**: [Docker] Remove redundant flashinfer download-cubin step (#46517)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ef361de](https://github.com/vllm-project/vllm/commit/ef361de9163e1d0fe8c0ea9028b320994c24f218)

- **作者**: Giancarlo Delfin
- **时间**: 2026-06-23T19:09:06Z
- **提交信息**: [Model Runer V2][DFlash] Fix lm head sharing for dflash (#46435)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [acce57d](https://github.com/vllm-project/vllm/commit/acce57d8dd8bed25543f8ece834a3757208c677c)

- **作者**: Yan Ma
- **时间**: 2026-06-23T18:53:38Z
- **提交信息**: Deprecate old FP8 online MoE quantization class (#44514)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [68afd78](https://github.com/vllm-project/vllm/commit/68afd7889723c1538af7993b6e568b01945ce43a)

- **作者**: peizhang56
- **时间**: 2026-06-23T18:45:31Z
- **提交信息**: [Bugfix][ROCm] Fix cumem sleep and teardown (#46203)

Signed-off-by: pei.zhang <pei.zhang@amd.com>
Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [37a682d](https://github.com/vllm-project/vllm/commit/37a682d392330da665690ee0a77c9d0a875f315f)

- **作者**: Michael Goin
- **时间**: 2026-06-23T18:45:10Z
- **提交信息**: [Kernel] Extend Marlin thread-tile padding to MoE (WNA16 + FP8/MXFP8) (#45703)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d8e422c](https://github.com/vllm-project/vllm/commit/d8e422ccda9b39ca8a0756b5b195513045abcee8)

- **作者**: Rui Yin
- **时间**: 2026-06-23T18:43:58Z
- **提交信息**: [Bugfix] Parse MiniMax M3 streaming reasoning by text markers (#45718)

Signed-off-by: test test <2260891073@qq.com>

### [e368415](https://github.com/vllm-project/vllm/commit/e368415daa2c4a4141904ec9c85e7a0dcaff6160)

- **作者**: fxmarty-amd
- **时间**: 2026-06-23T18:25:27Z
- **提交信息**: [AMD][OCP MX][CI] Fix tests to not dispatch on `UNFUSED_TRITON` backend on MI300, improve w_mxfp4_a_fp8 emulation support (#46142)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [ceae5bc](https://github.com/vllm-project/vllm/commit/ceae5bcbda06ac41ff76317c4475e8b1165e419e)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-23T18:11:40Z
- **提交信息**: [ROCm][CI] Fix nixl tests (#45219)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [6691f08](https://github.com/vllm-project/vllm/commit/6691f087a65bc161192ced91360bf11313828258)

- **作者**: Yongye Zhu
- **时间**: 2026-06-23T17:28:49Z
- **提交信息**: [Minimax-M3] BF16/FP8 Indexer using MSA (#45892)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [f4d5f73](https://github.com/vllm-project/vllm/commit/f4d5f73ffa402569ee76e5a2ade05ce7f8b5a843)

- **作者**: Priyansh Jain
- **时间**: 2026-06-23T16:56:17Z
- **提交信息**: [Bugfix]: Fix unquantized gpt-oss weight loading broken by FusedMoE r… (#45818)

Signed-off-by: priyansh jain <priyansh.jain2@amd.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [fd50a66](https://github.com/vllm-project/vllm/commit/fd50a66015b5b3095552be53ab7658b564458123)

- **作者**: fxmarty-amd
- **时间**: 2026-06-23T16:35:49Z
- **提交信息**: [CI][ROCm] Skip unsupported test cases on ROCm (#46160)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [84586c9](https://github.com/vllm-project/vllm/commit/84586c9acc0236fcee93fbbbb796ef50655d9484)

- **作者**: Divakar Verma
- **时间**: 2026-06-23T16:34:21Z
- **提交信息**: [ROCm][CI] fix fp8 range in vit_fp8_quant (#46410)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Signed-off-by: Divakar Verma <137818590+divakar-amd@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [40e5522](https://github.com/vllm-project/vllm/commit/40e552212126717cf59dd493c2057dfdd5a1259e)

- **作者**: Taneem Ibrahim
- **时间**: 2026-06-23T15:59:45Z
- **提交信息**: [Docs] Add Qwen3 forced alignment online example (#46197)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [f3410b3](https://github.com/vllm-project/vllm/commit/f3410b3bb16b1b0f33468a65f260148565c9948c)

- **作者**: Willow Lopez
- **时间**: 2026-06-23T15:46:23Z
- **提交信息**: fix(moe_wna16): access tp_size via moe_config for RoutedExperts compatibility (#45404)

Signed-off-by: Oxygen <1391083091@qq.com>
Signed-off-by: Willow Lopez <100782273+Oxygen56@users.noreply.github.com>

### [568874f](https://github.com/vllm-project/vllm/commit/568874fec2e6070684ee1a0547fe720dcf7322b9)

- **作者**: Divakar Verma
- **时间**: 2026-06-23T15:44:43Z
- **提交信息**: [ROCm][CI] pass merge-base to container for python-only wheel metadata (#45869)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [275b431](https://github.com/vllm-project/vllm/commit/275b43183c7253a45bd0214d165b0d5347de1ec6)

- **作者**: Martin Hickey
- **时间**: 2026-06-23T15:22:29Z
- **提交信息**: [MyPy] Fix mypy for `vllm/benchmarks` (#39896)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [547d2c4](https://github.com/vllm-project/vllm/commit/547d2c40d719e35d675405195053725a40e0351d)

- **作者**: Yan Ma
- **时间**: 2026-06-23T15:08:17Z
- **提交信息**: Add weights padding for fp8 per-block online quantization (#44763)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [2aaaf3f](https://github.com/vllm-project/vllm/commit/2aaaf3febdcc7248d4ef729f1224845a0163e527)

- **作者**: Spandan Tiwari
- **时间**: 2026-06-23T15:07:46Z
- **提交信息**: [ROCm][Test] Fix stale test_gfx950_moe MXFP4 oracle tests (#46260)

Signed-off-by: Spandan Tiwari <23646532+spandantiwari@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [156b126](https://github.com/vllm-project/vllm/commit/156b12667cf5fbb93914f3646acc25dca378b420)

- **作者**: Micah Williamson
- **时间**: 2026-06-23T14:26:39Z
- **提交信息**: [ROCm][CI] Skip Quark mxfp4 tests unless Quark version is compatible with Torch version (#46431)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [9f6f296](https://github.com/vllm-project/vllm/commit/9f6f2964287ae0a844b55f0c509c04d8fa139e2d)

- **作者**: Jee Jee Li
- **时间**: 2026-06-23T14:09:48Z
- **提交信息**: [CI/Build] Remove BaiChuanForCausalLM from the LoRA test (#46494)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [e51e700](https://github.com/vllm-project/vllm/commit/e51e700470cd04dbb25cb470571882dcbfed2a8a)

- **作者**: lcheng
- **时间**: 2026-06-23T14:08:33Z
- **提交信息**: [LoRA] Gate all_gather on fully_sharded_loras inside _mcp_apply; rewrite regression test (#45715)

Signed-off-by: lcheng <lcheng321@gatech.edu>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [f59db63](https://github.com/vllm-project/vllm/commit/f59db63732e5c4f72e64d524cecc87e6fe0c4453)

- **作者**: yzong-rh
- **时间**: 2026-06-23T13:36:33Z
- **提交信息**: [Bugfix] GPT-OSS Autodrop reasoning in Response API and cleanup (#45048)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Ben Browning <bbrownin@redhat.com>

### [9f51178](https://github.com/vllm-project/vllm/commit/9f5117820fb0e25ca76a1c7d0ec5c4c6766c4c4e)

- **作者**: Rukhaiya2004
- **时间**: 2026-06-23T13:24:49Z
- **提交信息**: [HARDWARE][POWER] Enable fp16 support for PowerPC (#46135)

Signed-off-by: Rukhaiya <bibirukhaiya123@gmail.com>

### [1bf149f](https://github.com/vllm-project/vllm/commit/1bf149f3348e4ac0283386c914c1aa15a8ce6e09)

- **作者**: Muhammad Fawaz
- **时间**: 2026-06-23T13:20:50Z
- **提交信息**: Filter Pydantic-internal markers from validation error param (#46457)

Signed-off-by: muhammadfawaz1 <135441198+muhammadfawaz1@users.noreply.github.com>
Co-authored-by: Mahad Rehmann <114791389+mahadrehmann@users.noreply.github.com>

### [2a675a7](https://github.com/vllm-project/vllm/commit/2a675a7b9fce6577e8eab937f67c7c1973a54f7f)

- **作者**: yzong-rh
- **时间**: 2026-06-23T12:54:46Z
- **提交信息**: [Bugfix] Responses API assistant EasyInputMessageParam input (#44361)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Ben Browning <bbrownin@redhat.com>

### [7d47cff](https://github.com/vllm-project/vllm/commit/7d47cff93380b7b20c903041b5204378f31ad758)

- **作者**: Itay Etelis
- **时间**: 2026-06-23T12:45:27Z
- **提交信息**: [Bugfix][KV Offload] Fix swap_blocks_batch on the default stream (#46379)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <Itay.etelis@gmail.com>

### [091bc10](https://github.com/vllm-project/vllm/commit/091bc1026ea4e5120893ae9a730fdb1bf5e873e2)

- **作者**: Srinivas Krovvidi
- **时间**: 2026-06-23T12:10:36Z
- **提交信息**: [KV Offloading] Add tiering metric plumbing (#45959)

Signed-off-by: srinivas_oo7 <sklinkedin0120@gmail.com>
Co-authored-by: srinivas_oo7 <sklinkedin0120@gmail.com>

### [3554ada](https://github.com/vllm-project/vllm/commit/3554ada5d82c50fc55a1ca98d169fafccc435827)

- **作者**: hillel.darshan
- **时间**: 2026-06-23T11:54:07Z
- **提交信息**: [CPU][Bugfix][Speculative Decoding] Accept USE_FP64_GUMBEL in CPU recovered-tokens sampler (#46069)

Signed-off-by: hillel.darshan <hillel.darshan@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [31ca950](https://github.com/vllm-project/vllm/commit/31ca9504b14c328291fda1ad1a2659180ae8eb34)

- **作者**: wang.yuqi
- **时间**: 2026-06-23T11:19:09Z
- **提交信息**: [Frontend] Split ServingRender into renderer and entrypoint. (#44285)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [d32575a](https://github.com/vllm-project/vllm/commit/d32575a2d2d83362a69d8bcf4544589cdbc11a9c)

- **作者**: Tan Pin Siang
- **时间**: 2026-06-23T10:33:23Z
- **提交信息**: [ROCm][P/D] Support MoRIIO heterogeneous TP fan-in (#46332)

Signed-off-by: Tan Pin Siang <tanpinsiang@gmail.com>
Co-authored-by: vllmellm <vllm.ellm@embeddedllm.com>
Co-authored-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: Jun Kang Chow <junkangchow@gmail.com>
Co-authored-by: Chun Fang <chun.fang@amd.com>
Co-authored-by: TianDi101 <ditian12@amd.com>
Co-authored-by: functionstackx <47992694+functionstackx@users.noreply.github.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [83fa302](https://github.com/vllm-project/vllm/commit/83fa302ca430592bbf547a20b818cc34c9f40e89)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-06-23T10:24:51Z
- **提交信息**: fix(security): prevent infinite loop in split_audio with NaN audio sa… (#46463)

### [20b5af5](https://github.com/vllm-project/vllm/commit/20b5af55c1c9ad0d1a00dc45771997dd490c8461)

- **作者**: frida-andersson
- **时间**: 2026-06-23T10:12:04Z
- **提交信息**: [ROCm][Perf] DSv3.2: fuse MLA Q concat+fp8-quant in forward_mqa (#43673)

Signed-off-by: Frida Andersson <fanderss@amd.com>

### [901a3b0](https://github.com/vllm-project/vllm/commit/901a3b091cf1c952ab582aefa6597e98f22055e5)

- **作者**: Qiming Zhang
- **时间**: 2026-06-23T08:59:11Z
- **提交信息**: fix gpt_oss pp>1 with ep (#46441)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>

### [2d721ab](https://github.com/vllm-project/vllm/commit/2d721ab5d82a2a2505480924c615187bd5b793c1)

- **作者**: Reid
- **时间**: 2026-06-23T08:32:33Z
- **提交信息**: [Rust Frontend] Align Rust allowed_token_ids validation with Python (#46348)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [accaa43](https://github.com/vllm-project/vllm/commit/accaa434f36b37a35b3e68eede167415ecc83c51)

- **作者**: Reid
- **时间**: 2026-06-23T08:04:41Z
- **提交信息**: [Rust Frontend]  Support echo for token-ID completion prompts (#46219)

Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: reidliu41 <reid201711@gmail.com>

### [a04654d](https://github.com/vllm-project/vllm/commit/a04654da23baf18d9513ed46d0f49b0e296d4623)

- **作者**: Sunny Yuan
- **时间**: 2026-06-23T07:42:27Z
- **提交信息**: Doc: fix missing GLM-5.x in supported models (#46452)

Signed-off-by: Sunny Yuan <y.zichen@wustl.edu>

### [25bc3be](https://github.com/vllm-project/vllm/commit/25bc3be49cc7ce8e7b185ca7da11b2fc9778832c)

- **作者**: Bugen Zhao
- **时间**: 2026-06-23T07:38:39Z
- **提交信息**: [Rust Frontend] Correct `--reasoning-parser` semantics (#46359)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [a46f3eb](https://github.com/vllm-project/vllm/commit/a46f3eb232b8a74bab0aab02b6a070ebf337125f)

- **作者**: Ting SUN
- **时间**: 2026-06-23T07:01:13Z
- **提交信息**: [Bugfix][Model Runner V2] Preserve all allowed_token_ids in the logit bias kernel (#46245)

Signed-off-by: Ting Sun <suntcrick@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-24
**监控日期**: 2026-06-23
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5250
- **最后更新**: 2026-06-23T23:04:23Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Zeyu Huang | 黃澤宇, SYLAR, wangyu

## AI分析总结

根据提供的提交记录，结合项目“Easy, fast, and cheap omni-modality model serving for everyone”的背景，以下是昨日更新的分析和总结：

---

### 1. 主要更新类型

- **Bug 修复**：提交 1 修复了 JoyVL 模型服务与参考引擎的对齐问题（包括长时记忆、时间戳、最大像素等）
- **文档/流程改进**：提交 2 为 bug 报告模板添加了字段 ID，以规范问题提交流程
- **功能新增**：提交 3 新增了流式扩散视频生成输出的能力

---

### 2. 关键变更点及其与项目整体方向的关系

| 提交 | 关键变更 | 与项目方向的关系 |
|------|----------|------------------|
| Fix JoyVL serving | 修复 JoyVL 服务中与参考引擎不一致的问题（长时记忆、时间戳、`max_pixels`） | 提升多模态模型（特别是视觉语言模型）服务的稳定性和正确性，直接服务于“省心”和“快速”目标 |
| Add field IDs to bug report | 标准化 issue 模板，增加字段 ID（方便追踪） | 改善开发流程，有助于社区协作和问题定位，间接提升项目维护效率 |
| Streaming diffusion video | 支持流式扩散视频生成输出 | 扩展多模态服务能力（视频生成），符合“omni-modality”愿景，使服务能实时生成视频 |

---

### 3. 对项目的影响和潜在意义

- **JoyVL 修复**：确保 JoyVL 模型的行为与参考引擎一致，避免因长时记忆机制、时间戳处理或像素限制导致的服务错误。这对于依赖 JoyVL 的用户（如多模态交互应用）至关重要，直接提升服务可靠性和用户体验。
- **问题模板改进**：统一 bug 报告格式，降低开发者和用户沟通成本，加速问题诊断与修复，提升项目可持续发展能力。
- **流式视频生成**：使 vllm-omni 能够以流式方式输出扩散模型生成的视频，这是多模态服务的重要扩展。实时视频生成在对话系统、创意工具、自动化内容生产等场景有巨大潜力，与项目“快速”和“低成本”目标一致（流式输出可减少延迟和内存占用）。

---

### 4. 值得关注的技术点

- **JoyVL 修复内容**：`bounded long-term memory` 和 `timestamps` 表明 JoyVL 可能使用了带有时间上下文的长时记忆机制，修复确保在服务场景下边界条件正确；`max_pixels` 涉及图像预处理时的像素上限，对齐后能避免因输入尺寸问题导致的性能或内存异常。
- **流式扩散视频生成**：将扩散模型的视频生成过程流式化，可能涉及到逐帧生成或 chunks 输出，这需要处理生成延迟、缓存管理和网络传输优化。这对架构中的后端推理引擎和前端协议提出了新挑战。

---

### 5. 基于项目背景，这些提交如何影响项目发展

- **持续完善多模态覆盖**：JoyVL 修复和视频流式生成分别加强了图像/视频理解和生成能力，朝着“任意模态”的服务目标迈进。
- **服务质量和可观测性提升**：问题模板标准化和修复工作体现了对服务质量（服务质量）的重视，有助于吸引更多开发者使用和贡献。
- **扩展实时应用场景**：流式视频输出使 vllm-omni 更适用于实时交互系统（如虚拟主播、实时内容生成），与“fast”和“cheap”愿景一致（流式可降低端到端延迟和峰值资源消耗）。
- **社区协作优化**：模板改进是长期维护健康的体现，为后续更大规模的功能开发和社区贡献打下基础。

---

**总结**：昨日更新以 **修复 JoyVL 服务一致性** 和 **新增流式视频生成功能** 为核心，前者提升了现有模型服务的可靠性，后者拓展了项目在多模态生成领域的边界。同时，问题模板的改进优化了开发效率。这些更新共同推动了 vllm-omni 在“易用、快速、低成本的多模态服务”方向上的稳步发展。

## 详细提交记录

### [d35cdd2](https://github.com/vllm-project/vllm-omni/commit/d35cdd2dabb6bc8f5321a2c0c972d4ef1497e42e)

- **作者**: SYLAR
- **时间**: 2026-06-23T23:04:17Z
- **提交信息**: [Fix] JoyVL serving: align with reference engine (bounded long-term memory, timestamps, max_pixels) + recipe updates (#4623)

Signed-off-by: lishunyang12 <125541396+lishunyang12@users.noreply.github.com>

### [0958e62](https://github.com/vllm-project/vllm-omni/commit/0958e62eccbfe833313c7d211c104d8e2aed9460)

- **作者**: wangyu
- **时间**: 2026-06-23T12:26:25Z
- **提交信息**: Add field IDs to bug report issue template (#4605)

Signed-off-by: wangyu <410167048@qq.com>

### [3901ad8](https://github.com/vllm-project/vllm-omni/commit/3901ad816554b13a48545fbc892c9648987d4ac2)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-06-23T09:57:53Z
- **提交信息**: [feat] Streaming diffusion video generation output (#3737)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Signed-off-by: Zeyu Huang | 黃澤宇 <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

---
