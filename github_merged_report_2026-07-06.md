# GitHub Stars 合并报告 - 2026-07-06

**合并日期**: 2026-07-07
**监控日期**: 2026-07-06
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


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2064
- **最后更新**: 2026-07-06T08:13:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2468
- **最后更新**: 2026-07-06T22:21:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2160
- **最后更新**: 2026-07-06T15:40:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5909
- **最后更新**: 2026-07-06T19:20:24Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Jimmy Zhou, Albert Cheng

## AI分析总结

以下是根据提交记录和中英文README背景进行的分析总结：

### 1. 主要更新类型
- **项目管理/团队配置**（非功能、非Bug、非性能、非文档）

### 2. 关键变更点及其与项目整体方向的关系
- **提交 `a5a8051`**：将 `@qiching` 添加为核心维护者（`CODEOWNERS` 中针对全局路径）
- **提交 `736549e`**：手动为 `fmhav2` 相关文件/目录添加代码所有者（`CODEOWNERS`）
- 两者均不涉及代码逻辑变更，属于**仓库权限与审查责任划分**的调整  
- 与项目方向的关系：FlashInfer 专注于提供高性能 GPU 推理内核，代码质量和审查流程对保证内核正确性与性能至关重要。明确代码所有者有助于加速 PR 审查、降低知识孤岛风险，是该类基础软件项目健康发展的必要管理动作。

### 3. 对项目的影响和潜在意义
- **短期影响**：无可见功能或性能变化
- **中期意义**：
  - 强化核心团队的审查能力，尤其是 `@qiching` 作为新增核心维护者，可能将负责多个关键模块
  - 针对 `fmhav2` 的专用代码所有者，确保该特定注意力变体（FlashAttention v2?）的更改由熟悉该模块的人把关
  - 提升社区协作效率，减少 PR 积压

### 4. 值得关注的技术点
- **无技术性变更**，但 `fmhav2` 可能对应 `flash_attention_v2` 相关内核，表明该项目在持续维护核心注意力算子
- 两个提交均通过 GitHub PR 模板标准流程，说明团队已建立规范的贡献审查制度

### 5. 基于项目背景（高性能 GPU 推理内核）的提交影响
- FlashInfer 的目标是提供“高性能 GPU 推理内核”，此类项目对代码质量、测试覆盖和性能回归极为敏感。通过明确代码所有者：
  - 可确保对关键内核（如 attention, moe 等）的改动得到有经验的维护者审查
  - 减少因人员流动导致的维护断层，有利于项目长期迭代
  - 对社区贡献者而言，清晰的所有者列表也能指导他们选择合适的 reviewer，提升贡献体验

> 总结：昨日更新属于**项目管理与团队扩展**，并非功能开发。其核心价值在于优化开源协作流程，保障后续高性能内核开发的审查效率与质量，间接推动项目稳定发展。

## 详细提交记录

### [a5a8051](https://github.com/flashinfer-ai/flashinfer/commit/a5a8051bbed69ff2c94b1e5f112607f16ef9ab1f)

- **作者**: Albert Cheng
- **时间**: 2026-07-06T18:52:39Z
- **提交信息**: chore: add @qiching to core maintainers in CODEOWNERS (#3851)

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
* Updated review ownership settings for uncategorized repository paths.
No user-facing product changes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Albert Cheng (Engrg-Hardware 1) <albecheng@login-bia01.bia.clusters.nvidia.com>

### [736549e](https://github.com/flashinfer-ai/flashinfer/commit/736549e150f4c3aef37bd69da3cebe7b2092e57f)

- **作者**: Jimmy Zhou
- **时间**: 2026-07-06T17:59:01Z
- **提交信息**: chore: manual add to codeowners for fmhav2 (#3816)

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

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3801
- **最后更新**: 2026-07-06T19:07:31Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **持续集成/测试基础设施增强**（`[ci]`）
- **Bug修复**（`[bugfix]`）

#### 2. 关键变更点及其与项目方向的关系
- **`a25313b`**：将 `fastvideo/tests/ops/` 目录下的操作测试接入单元测试流水线。  
  → 符合项目“快速启动”和文档化的方向，通过自动化测试确保核心操作的可靠性，降低开发者引入回归的风险。
- **`dbde643`**：将 Flash Attention 4（FA4）的依赖版本固定到与 CuTe DSL 4.6 兼容的修订版。  
  → 解决依赖兼容性 bug，确保高性能注意力机制在最新 CUDA 工具链下稳定运行，直接支撑视频生成/处理中的长序列高效计算。

#### 3. 对项目的影响和潜在意义
- **代码质量提升**：新增 CI 测试覆盖 `tests/ops`，减少未来操作模型的手工验证负担。
- **稳定性修复**：消除 FA4 与 CuTe DSL 4.6 的不兼容问题，避免用户在特定硬件/驱动环境下出现运行时崩溃。
- **维护性改善**：显式版本锁定使得构建环境可复现，方便社区贡献者复现问题。

#### 4. 值得关注的技术点
- **CuTe DSL 4.6 兼容性**：CuTe 是 NVIDIA 的线性代数模板库，此次更新意味着 FastVideo 正在适配较新的 CUDA 内核基础设施，可能为后续支持 Blackwell 架构做准备。
- **FA4 版本锁定策略**：固定 pin 而非宽松版本，表明团队倾向于严格控制依赖以避免意外破坏，这对机器学习库的长期维护至关重要。

#### 5. 基于项目背景的发展影响
- README 强调“文档”和“快速开始”，这两次提交间接支持了该目标：  
  - 单元测试覆盖确保文档中的示例代码可正常运行；  
  - Bug 修复让用户在快速上手时不会因依赖兼容性而受阻。
- 作为以“Fast”命名的视频加速库，保持依赖与最新 CUDA 生态同步是核心竞争力，此次修复有助于保持性能领先性。
- 测试基础设施的完善为未来引入更多特性（如分布式训练、视频数据集加载等）提供了质量保障。

## 详细提交记录

### [a25313b](https://github.com/hao-ai-lab/FastVideo/commit/a25313beec11965fce04321b9560b58bcb867504)

- **作者**: William Lin
- **时间**: 2026-07-06T19:07:26Z
- **提交信息**: [ci]: wire fastvideo/tests/ops/ into the unit-test lane (#1559)

### [dbde643](https://github.com/hao-ai-lab/FastVideo/commit/dbde64385bf638ae969b76dd3f2329e67e4006f8)

- **作者**: William Lin
- **时间**: 2026-07-06T19:06:59Z
- **提交信息**: [bugfix]: bump FA4 pin to the CuTe DSL 4.6 compatible rev (#1564)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33995
- **最后更新**: 2026-07-06T20:59:53Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Mishig

## AI分析总结

好的，我们来分析 `huggingface/diffusers` 仓库昨日唯一的提交记录。

### 1. 主要更新类型
- **性能优化**：核心目标是加快文档构建速度。
- **文档/CI 流程优化**：具体通过调整 CI 工作流来实现（轻量安装、移除自定义容器）。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：
  - 更新文档构建工作流（`doc build workflow`）：改用轻量级安装方式，移除自定义 Docker 容器。
  - 保持依赖锁定注释的兼容性，以便与自动依赖更新机器人（Dependabot）配合。
- **项目方向**： `diffusers` 是一个活跃的开源项目，文档质量与更新速度直接影响用户（尤其是新手）的上手体验和社区贡献效率。**减少构建时间** 能加速文档部署迭代，让最新功能说明更快展示，符合项目“易用、开放”的核心理念。

### 3. 对项目的影响和潜在意义
- **积极影响**：
  - 缩短 CI 流水线时间，降低贡献者对文档 PR 的等待时长。
  - 移除自定义容器可减少维护复杂度，标准化部署环境。
  - 依赖锁定与 Dependabot 兼容，能自动、安全地更新依赖，减少人工疏忽。
- **潜在意义**：体现了项目团队对开发者体验（DX）的持续优化，即使是非功能性的 CI 改进，也能提升整体开发效率。

### 4. 值得关注的技术点
- **轻量安装**：可能指只安装文档构建所需的最小依赖（如 Sphinx、特定主题），而非全量库依赖。这是一种 **按需构建** 策略，类似 `pip install .[docs]` 而非 `pip install -e .`。
- **移除自定义容器**：改用 GitHub Actions 内置环境或更标准化的容器，降低自定义层带来的 bug 风险，也便于后续迁移或复用其他工作流模板。
- **Dependabot 兼容**：通过合理的注释（`# pin comment`）让自动更新机器人能轻易定位并升级依赖版本，体现了 CI 配置的长期可维护性。

### 5. 结合项目背景，对项目发展的影响
- 根据 README，扩散模型（如 Stable Diffusion）迭代极快，新 pipeline、新调度器、新模型不断加入。**文档是项目的“门面”**，快速构建能让文档与代码同步，避免用户看到过时内容。
- 该提交虽小，但传递了项目维护者重视基础设施优化的信号——**稳定的 CI 是开源项目可持续发展的基石**。它解放了核心开发者手动处理文档部署的时间，让他们更专注于模型与 API 的研发，从而加速 `diffusers` 在生成式 AI 领域保持领先地位。

## 详细提交记录

### [a7166ce](https://github.com/huggingface/diffusers/commit/a7166cee37e9f7f912e60968f55a136dd599bc8d)

- **作者**: Mishig
- **时间**: 2026-07-06T14:18:24Z
- **提交信息**: Make doc builds faster (#14131)

* Update doc build workflow: light installs, drop custom container

* Update doc build workflow: light installs, drop custom container

* Keep the pin comment dependabot-compatible

* Keep the pin comment dependabot-compatible

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 423
- **最后更新**: 2026-07-03T19:24:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12668
- **最后更新**: 2026-07-06T14:08:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29991
- **最后更新**: 2026-07-06T22:02:20Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 12
- **主要提交者**: Chetan Kumar Verma, Lijuan Tang, Aditya Kamat

## AI分析总结

根据昨日提交记录，结合 **SGLang** 项目（一个高性能推理框架，支持 LLM 和扩散模型，注重多硬件适配与性能优化）的背景，总结如下：

---

### 1. 主要更新类型
- **功能新增**：W4A8 MXFP 量化支持、扩散模型跨注意力 KV 缓存、NUMA 绑定回退、OCR 模型精度基准
- **Bug 修复**：Mamba 长前缀缓存恢复精度、NVFP4 路由 GEMM 数值精度与校正偏置转换、MLX 测试桩、ROCm 上 layernorm torch.compile 内存访问错误、AMD DeepSeek V4 sparse prefill 标志
- **性能优化**：Flashinfer allreduce 融合（全注意力 TP 时）、扩散测试新增、NPU 夜测改进
- **文档更新**：cookbook 添加总吞吐与分位延迟标签
- **重构/适配**：Ascend NPU 量化支持、NPU 测试用例同步

---

### 2. 关键变更点与项目方向关系

| 变更 | 对应项目方向 |
|------|-------------|
| W4A8 MXFP 量化 (Qwen3 Dense) | 扩展 NPU 硬件算力支持，降低推理显存占用 |
| 扩散模型跨注意力缓存 | 提升扩散模型（Helios）推理效率，契合项目扩散模型支持定位 |
| NVFP4 精度修复 | 强化混合精度推理稳定性，覆盖新数值格式 |
| Flashinfer allreduce 融合 | 利用硬件加速通信，降低 TP 推理延迟 |
| NUMA 回退机制 | 提升大模型多节点部署的鲁棒性 |
| OCR 精度基准 | 拓展模型评估维度，加强项目在视觉领域的应用 |

---

### 3. 对项目的影响与潜在意义
- **硬件生态扩展**：NPU (Ascend) 上的量化与测试改进，配合 AMD ROCm 修复，巩固 SGLang 在非 NVIDIA 硬件的竞争力。
- **推理效能提升**：Flashinfer 融合和扩散缓存优化直接降低延迟，对在线服务场景价值大。
- **稳定性增强**：NUMA 回退、Mamba 缓存 bug 修复提升了长序列推理的可靠性。
- **数值精度保障**：NVFP4 修复避免错误传播，对低比特推理落地至关重要。
- **易用性提升**：文档增加吞吐和延迟标签，帮助用户更准确评估性能。

---

### 4. 值得关注的技术点
- **MXFP W4A8**：在 Ascend NPU 上首次支持混合精度4bit权重+8bit激活的量化 (Qwen3)，可能成为低资源部署的优选方案。
- **Flashinfer Allreduce 融合**：在全注意力 TP 场景下，将线性层和注意力层的 allreduce 合并，减少通信次数，对长上下文模型收益明显。
- **Diffusion 跨步骤 KV 缓存**：Helios 模型的跨去噪步缓存，减少重复计算，类似 LLM 的 prefix caching 思想。
- **NUMA 绑定回退**：检测 `numactl --membind` 失败时自动改用其他策略，提升在复杂 NUMA 环境中的部署鲁棒性。

---

### 5. 从项目背景看发展影响
- **多硬件驱动**：大量 NPU、AMD、MLX 相关提交说明项目正从 NVIDIA 主导走向多硬件兼容，符合“快速推理引擎”定位。
- **性能与精度并重**：FP4、量化、Flashinfer 等提交体现项目在高吞吐与低精度推理之间的平衡追求。
- **模型支持多元化**：除了 LLM，扩散模型、OCR 模型的更新表明 SGLang 正拓展到多模态生成场景。
- **社区协作活跃**：多个外部贡献者（如 Elizaveta, ronnie_zheng, Brayden, Mingfei Ma 等）参与，反映项目生态良好。

## 详细提交记录

### [1c23954](https://github.com/sgl-project/sglang/commit/1c23954cb9e7073525f4306ca4c59f852f1d5c97)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-07-06T21:40:26Z
- **提交信息**: [NPU] Add new diffusion tests  (#29331)

Co-authored-by: Elizaveta Martirosian <elizaveta.martirosian@gmail.com>

### [093256a](https://github.com/sgl-project/sglang/commit/093256aa4b450b6e4323e5b82796abc4f8a83cef)

- **作者**: Aditya Kamat
- **时间**: 2026-07-06T20:57:44Z
- **提交信息**: [Mamba] Fix long-prefill accuracy drop in radix prefix-cache state restore (#29368)

### [ca73c77](https://github.com/sgl-project/sglang/commit/ca73c7705592e2c175c2a5d53f1b195a364bd95b)

- **作者**: Thomas
- **时间**: 2026-07-06T20:56:37Z
- **提交信息**: [Diffusion] cache cross-attn K/V across denoise steps for Helios (#29755)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [d8462f4](https://github.com/sgl-project/sglang/commit/d8462f496194772b5adb8ba0e2dc9ddb5c9a3e6d)

- **作者**: Brayden Zhong
- **时间**: 2026-07-06T20:53:05Z
- **提交信息**: Fixes for NVFP4 numerical accuracy for router GEMM output and wrong correction bias cast (#29783)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [1579a82](https://github.com/sgl-project/sglang/commit/1579a82d17e0650b61327e226f489fc4dcdbb21f)

- **作者**: Lijuan Tang
- **时间**: 2026-07-06T20:43:40Z
- **提交信息**: [MLX] Fix FakeOverlapScheduler test stub broken by forward_ct accounting (#30125)

### [8f40b5e](https://github.com/sgl-project/sglang/commit/8f40b5eb3f59e031bfa9fd161a240aaf50444172)

- **作者**: Brayden Zhong
- **时间**: 2026-07-06T20:01:53Z
- **提交信息**: When attention TP for linear and full attention, use Flashinfer allreduce fusion (#29699)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [52c6e27](https://github.com/sgl-project/sglang/commit/52c6e27e7e59405a6db38a871df229cc4a512ac6)

- **作者**: sushil Dubey
- **时间**: 2026-07-06T18:15:57Z
- **提交信息**: [AMD][diffusion] fix: disable layernorm torch.compile decorator in eager mode on ROCm to avoid memory-access fault (#29673)

### [3abdbab](https://github.com/sgl-project/sglang/commit/3abdbab9bbb4ef960be30809a62affd6c6d7a38f)

- **作者**: Junlin Wu
- **时间**: 2026-07-06T16:23:26Z
- **提交信息**: :sparkles: [llm][npu][quant] Add W4A8 MXFP quantization support for Qwen3 Dense on Ascend NPU (#23650)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [1b481de](https://github.com/sgl-project/sglang/commit/1b481deade53fd23ed787c4dbd5f389b1455a7b2)

- **作者**: hhhh1252023
- **时间**: 2026-07-06T14:41:15Z
- **提交信息**: feat: sync npu nightly test improvements from Ascend testcases (#29403)

### [80decc7](https://github.com/sgl-project/sglang/commit/80decc78ec226ec168977406277fec707c96b718)

- **作者**: Thomas Wang
- **时间**: 2026-07-06T08:25:55Z
- **提交信息**: [AMD][DeepSeek V4] Set SGLANG_OPT_FLASHMLA_SPARSE_PREFILL to false on hip code path (#30237)

### [b3ab565](https://github.com/sgl-project/sglang/commit/b3ab56545b656796d4f48212090077649ac12107)

- **作者**: Chetan Kumar Verma
- **时间**: 2026-07-06T08:18:43Z
- **提交信息**: Add Accuracy Benchmark for OCR models (#25364)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [e2b55bd](https://github.com/sgl-project/sglang/commit/e2b55bdbabf7d74cedde8b11c71f1d2d928df254)

- **作者**: chengcuiping
- **时间**: 2026-07-06T08:03:59Z
- **提交信息**: NUMA: probe numactl binding and fall back when --membind is rejected (#28401)

Co-authored-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [7c9bb31](https://github.com/sgl-project/sglang/commit/7c9bb316cf9ed2e61b61c9c595f2032324950827)

- **作者**: zijiexia
- **时间**: 2026-07-06T07:39:48Z
- **提交信息**: docs(cookbook): total (input+output) throughput per GPU + percentile latency labels (#30214)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1220
- **最后更新**: 2026-07-06T13:24:34Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

### 1. 主要更新类型
- **功能新增**：支持集成 `AnyFlow` 与 `AnyFlow-FAR` 两条新流水线（Pipeline），为 DiT 生态拓展新的模型接入。

### 2. 关键变更点及其与项目整体方向的关系
- **AnyFlow（双向扩散）**：完整支持缓存（Cache）、上下文并行（CP）和张量并行（TP），与 cache-dit 的核心能力（缓存+并行）高度契合。  
- **AnyFlow-FAR（因果自回归）**：由于逐块 AR 循环、每块调度器重置与全缓存预填充机制不兼容 cache-dit 的单步跟踪逻辑，**不支持缓存和 CP**，仅支持 TP（需特殊适配：保留 flex attention 后端、调整注意力头数等）。  
- **BlockAdapter 模式（Pattern_2）**：统一解析两类 Transformer 块，使 TP 通道能够正确定位模型组件，体现项目“适配器+解耦”的设计哲学。  
- **CLI 示例**：新增 `anyflow_t2v` 和 `anyflow_far` 命令行用例，降低用户接入门槛，推动项目向“开箱即用”发展。

### 3. 对项目的影响和潜在意义
- **扩大模型兼容范围**：引入业界最新的 AnyFlow 系列，增强 cache-dit 在视频生成（V2V/T2V）场景的竞争力。  
- **明确能力边界**：对因果 AR 流水线坦诚标注“不支持缓存/CP”，避免用户误用，提升项目可信度。  
- **推动并行策略适配**：为后续支持更复杂的因果结构（如 DiT-based AR）提供技术参考（TP+flex attention 共存方案）。

### 4. 值得关注的技术点
- **CP 的混合根分割 + RoPE 偏移补丁 + 解包补丁 + attention processor 补丁**：为 AnyFlow 定制的上下文并行实现，展示了 cache-dit 的分层补丁机制。  
- **TP 标准 MHA 方案**：使用 `ColwiseParallel` 处理 Q/K/V，`RowwiseParallel` 处理 to_out/FFN 及 `DistributedRMSNorm`，保持与主流框架的一致性。  
- **FAR 的 TP 特殊处理**：`config.num_attention_heads //= tp_size` 确保 KV cache 尺寸正确；`flex attention` 原生保留以避免被原生 attention 覆盖。  
- **BlockAdapter 统一寻址**：即使 `cache_config is None`（仅 TP 流），也能通过适配器找到 transformer，体现了模块化设计。

### 5. 这些提交如何影响项目发展（结合 README 背景）
- **加速“PyTorch 原生推理引擎”目标**：通过灵活适配器模式接入新模型，保持纯 PyTorch 生态兼容性，无需引入自定义 CUDA 核。  
- **强化“缓存+并行”核心卖点**：AnyFlow 的完整支持验证了 cache-dit 对现代扩散变压器的通用加速能力，而 FAR 的受限支持则反向提醒用户选择最适合的推理策略。  
- **提升社区吸引力**：增加主流视频生成模型的支持（AnyFlow 在任意长度视频生成上有优势），配合 PyPI 下载量增长，加速项目从工具向平台化演进。

## 详细提交记录

### [c8c22af](https://github.com/vipshop/cache-dit/commit/c8c22afc99e4c7482786dc4c61d61b5868e098d3)

- **作者**: DefTruth
- **时间**: 2026-07-06T07:19:00Z
- **提交信息**: feat: support AnyFlow & AnyFlow-FAR (#1081)

* update skill

* feat: support AnyFlow & AnyFlow-FAR pipeline integration

Add cache-dit integration for the AnyFlow family (bidirectional + FAR causal):

AnyFlow (bidirectional, AnyFlowPipeline):
- BlockAdapter (Pattern_2), Cache/CP/TP all supported
- CP: hybrid root-split + RoPE offset patch + unpack patch + attn processor patch
- TP: standard MHA plan (ColwiseParallel Q/K/V, RowwiseParallel to_out/FFN, DistributedRMSNorm)
- CLI: anyflow_t2v example

AnyFlow-FAR (causal AR, AnyFlowFARPipeline):
- Cache: NOT supported (chunk-wise AR loop + per-chunk scheduler reset +
  mandatory full cache-prefill passes are incompatible with cache-dit's
  single-trajectory step tracking)
- CP: NOT supported (causal flex_attention BlockMask + cross-chunk KV cache
  are broken by Ulysses sequence-split)
- TP: supported via AnyFlow planner with FAR-specific adaptations:
  - patch config.num_attention_heads //= tp_size so the pipeline allocates a
    correctly-sized per-rank KV cache (transformer.forward uses attn.heads,
    not config, so it is unaffected)
  - preserve the flex backend on AnyFlowCausalAttnProcessor (BlockMask requires
    flex; cache-dit TP dispatch would otherwise overwrite it to native)
- BlockAdapter resolves the FAR transformer too (same AnyFlowTransformerBlock,
  Pattern_2) so TP-only flows (cache_config is None) can locate the transformer
- TE-P (UMT5EncoderModel) and VAE-P (AutoencoderKLWan) already supported
- CLI: anyflow_far example (T2V, 81 frames, 4 steps)

Co-authored-by: Copilot <copilot@github.com>

---------

Co-authored-by: Copilot <copilot@github.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 85521
- **最后更新**: 2026-07-06T22:13:44Z

## 提交统计

- **昨日提交总数**: 40
- **提交者数量**: 34
- **主要提交者**: xiaozhoupy, Nick Hill, Andreas Karatzas

## AI分析总结

以下是针对 `vllm-project/vllm` 仓库昨日提交记录的分析总结，结合项目“简单、快速、便宜的 LLM 服务”背景进行评估。

---

### 1. 主要更新类型
- **Bug 修复**：占比最大（约 40%），覆盖 ROCm、XPU、模型层、分布式、调度等多个模块。
- **性能优化**：约 20%，包括内核缓存、图像预处理融合、模型后端加速、指标缓存等。
- **新功能/后端**：约 15%，如 Rust 前端指标缓存、新的量化后端（Humming MoE、B12x）、Helion 内核、AITER 自定义 all-reduce。
- **CI/构建改进**：约 15%，包括修复主分支错误、增加测试并行度、添加 agent 标签等。
- **安全/文档/重构**：少量，安全修复（阻止错误视频后端选择）、文档澄清、死代码清理。

---

### 2. 关键变更点及与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
|------------|----------------|
| **ROCm 生态增强**：Rust 前端标准化、AITER 替换、并行度提升 | 强化对 AMD GPU 的支持，符合“便宜”原则（利用非 NVIDIA 硬件） |
| **DeepSeek 模型支持优化**：FP8 KV cache reshape、draft_id 修复、token_to_req_indices 缓存（性能提升 5~6x） | 服务流行开源模型，提升性价比 |
| **新量化后端**：Humming MoE、B12x（Nemotron） | 扩展低成本部署选项，降低内存占用 |
| **Transformers 后端加速**：与原生 vLLM 速度对齐 | 核心性能目标，降低切换成本 |
| **安全与稳定性**：阻止请求级 GPU 后端选择、修复数值溢出与内存访问错误 | 保证生产可靠性，符合“简单”（可靠） |
| **XPU/Intel GPU 修复**：Triton attention 路由、权重加载 bug | 扩大硬件覆盖，适配多样化部署 |

---

### 3. 对项目的影响和潜在意义
- **影响范围**：修复关键错误可直接减少用户挂起和崩溃（如 DP MTP hang、int32 溢出），提升下游服务稳定性。
- **性能提升**：Kimi 图像预处理融合、DeepSeek 内核缓存等优化可显著降低延迟和吞吐成本，符合“快而便宜”。
- **硬件兼容性**：AMD/Intel GPU 的大量修复和 CI 改进使 vLLM 成为真正的多厂商方案，避免供应商锁定。
- **未来趋势**：Rust 前端和指标缓存的引入预示着更高效的监控和更轻量的生产部署。

---

### 4. 值得关注的技术点
- **Rust 前端缓存**：`cache metric handles` 可能为未来 Rust 化更多组件铺路，提升关键路径性能。
- **AITER 自定义 all-reduce**：在 ROCm 上直接实现通信算子，减少对 NCCL 的依赖，适用于大规模部署。
- **B12x 量化后端**：为非门控 MoE（如 Nemotron）提供专门优化，暗示 vLLM 在 MoE 模型上的持续投入。
- **负载均衡 tie-break 旋转**：避免系统性偏差，对多卡/多机部署有意义。

---

### 5. 结合项目背景分析：这些提交如何影响项目发展
- **强化核心承诺**：性能优化（Transformers 后端加速、内核缓存）直接兑现“

## 详细提交记录

### [8484ca5](https://github.com/vllm-project/vllm/commit/8484ca5d456acb716b3a6a7f4871709506139d61)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-06T22:05:39Z
- **提交信息**: [ROCm][CI] Adding Rust parity (#47478)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [482e552](https://github.com/vllm-project/vllm/commit/482e5524fe12b2793ae3a9d861754ffd4cee10ca)

- **作者**: Simon Danielsson
- **时间**: 2026-07-06T21:30:02Z
- **提交信息**: [Bugfix][ROCm] Fix memory access fault in AITER MLA backend for DPA+FP8 KV  (#47276)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Co-authored-by: nnyrhila <niko.nyrhila@amd.com>

### [567a784](https://github.com/vllm-project/vllm/commit/567a78432d8e00ac17e4288a4c15ca795c6a1bb4)

- **作者**: SherryC41
- **时间**: 2026-07-06T21:08:17Z
- **提交信息**: [Bugfix] Fix dp mtp hang (#40589)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: sherryC41 <sherry.c.c41@gmail.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [d891b9b](https://github.com/vllm-project/vllm/commit/d891b9bd51ce726a1bff24a72d03090057718789)

- **作者**: Jinzhen Lin
- **时间**: 2026-07-06T20:36:07Z
- **提交信息**: [Quantization] add humming moe backend to all dense/moe oracles (#41652)

Signed-off-by: Jinzhen Lin <jinzhen.ljz@antgroup.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [04adc88](https://github.com/vllm-project/vllm/commit/04adc8843bbe0711fed8edf50d6d4cd4fca400e7)

- **作者**: Zhiyi Hong
- **时间**: 2026-07-06T19:56:44Z
- **提交信息**: [Bugfix]Fix DeepSeek-V4 fp8_ds_mla KV cache reshape (#47716)

Co-authored-by: yy-fighting <23518844576@qq.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [ae098ab](https://github.com/vllm-project/vllm/commit/ae098abe3fffedd7acecc04265a10dc5624efdca)

- **作者**: Harry Mellor
- **时间**: 2026-07-06T19:40:23Z
- **提交信息**: [CI] Fix some errors on `main` (#47726)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [b1384f5](https://github.com/vllm-project/vllm/commit/b1384f5ec6b03140fda8c291aec07d35ce3d5c4c)

- **作者**: Andrii Skliar
- **时间**: 2026-07-06T19:40:07Z
- **提交信息**: Enable B12x backend for non-gated MoEs (like Nemotron)  (#43328)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>

### [b136cc2](https://github.com/vllm-project/vllm/commit/b136cc2c2c590593c9dfff2bd732edbb24bcceeb)

- **作者**: Nathaniel McVicar
- **时间**: 2026-07-06T19:39:12Z
- **提交信息**: [Bugfix][Model] Add stability window to DiffusionGemma to match HF stability_threshold semantics (#45965)

Signed-off-by: Nathaniel McVicar <namcvica@microsoft.com>
Signed-off-by: Nathaniel McVicar <Nathaniel.McVicar@microsoft.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [9fde043](https://github.com/vllm-project/vllm/commit/9fde043f5452b2aa49c90ddeb4848e0834aa32eb)

- **作者**: Xiaohong (Sean) Chen
- **时间**: 2026-07-06T16:19:01Z
- **提交信息**: [Kernel][Helion][1/N] Add Helion kernel for silu_and_mul_per_block_quant (#43994)

Signed-off-by: Sean Chen <seachen@redhat.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [24dd2ae](https://github.com/vllm-project/vllm/commit/24dd2aec81d780b9d3085fbc83fa81af970a3ba8)

- **作者**: lcheng
- **时间**: 2026-07-06T16:16:46Z
- **提交信息**: [Bugfix] Preserve FP8 indexer WK pairs across incremental load_weights (#46168)

Signed-off-by: lcheng <lcheng321@gatech.edu>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [3ee9eea](https://github.com/vllm-project/vllm/commit/3ee9eea9284c4fbe71459dec07063244e1b0ec75)

- **作者**: Ranran
- **时间**: 2026-07-06T15:59:16Z
- **提交信息**: [macOS][CPU][Installation] Fix the broken installation of vllm 0.24.0 in macos + cpu (#47457)

Signed-off-by: Ranran Haoran Zhang <ranranhaoranzhang@gmail.com>

### [5bce653](https://github.com/vllm-project/vllm/commit/5bce653e09ca62c870ea18d01a4180dc48d3bacb)

- **作者**: Harry Mellor
- **时间**: 2026-07-06T15:59:14Z
- **提交信息**: Make the Transformers modeling backend as fast as native vLLM (#47187)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5ad1117](https://github.com/vllm-project/vllm/commit/5ad11172b791104f2d9df3c7877a53a5aeb28878)

- **作者**: Kevin_Xiong
- **时间**: 2026-07-06T15:46:32Z
- **提交信息**: [perf]Add fused Kimi image preprocessing (#47416)

Signed-off-by: Kevin-XiongC <kevin_xiong1997@outlook.com>
Signed-off-by: Kevin_Xiong <kevin_xiong1997@outlook.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Isotr0py <2037008807@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [f70caef](https://github.com/vllm-project/vllm/commit/f70caef48b9263e8f86fdf20a04a4933a5f75083)

- **作者**: Wentao Ye
- **时间**: 2026-07-06T15:17:46Z
- **提交信息**: [Perf] Cache `token_to_req_indices` for dsv4, 5x~6x kernel performance improvement (#47474)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [8d8ec38](https://github.com/vllm-project/vllm/commit/8d8ec383619d956b25611a3312a431c9a6ca1c04)

- **作者**: Laurent-Zhang
- **时间**: 2026-07-06T14:55:47Z
- **提交信息**: [Bugfix][Spec Decode] Add missing draft_id_to_target_id to DSparkDeepseekV4ForCausalLM (#47429)

Signed-off-by: Laurent-Zhang <zhangdongsheng80@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b1c6dba](https://github.com/vllm-project/vllm/commit/b1c6dba558a5fec95fa1586b0b824755a367a93c)

- **作者**: Wentao Ye
- **时间**: 2026-07-06T14:54:08Z
- **提交信息**: [Refactor] Remove multiple dead code (#47329)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [598d511](https://github.com/vllm-project/vllm/commit/598d51153a15ff4a803037dade1c4ea43d1ea9bc)

- **作者**: jesco
- **时间**: 2026-07-06T14:47:06Z
- **提交信息**: [Bugfix][Distributed] Delegate MNNVL allreduce one-shot selection (#47589)

Signed-off-by: jesco-absolut <team@srswti.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [095adf1](https://github.com/vllm-project/vllm/commit/095adf1fdc93d5554a3afbf26e97b399309c80db)

- **作者**: Yifan Qiao
- **时间**: 2026-07-06T14:36:15Z
- **提交信息**: [Bugfix] Fix int32 overflow in triton_decode_attention page offsets (#47671)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>

### [51ee564](https://github.com/vllm-project/vllm/commit/51ee564e56312a8b3a17db4614f3e95cc33eb7f3)

- **作者**: Harry Mellor
- **时间**: 2026-07-06T14:24:09Z
- **提交信息**: [CI] Skip test for checkpoint that was deleted (#47748)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [373eb31](https://github.com/vllm-project/vllm/commit/373eb314af66559f9ef9d6b50bc2cb835012ef34)

- **作者**: Ting SUN
- **时间**: 2026-07-06T13:50:38Z
- **提交信息**: [Bugfix][Core] Fix num_output_placeholders underflow with async scheduling + spec decode (#46066)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [641cb59](https://github.com/vllm-project/vllm/commit/641cb595928a8914a7020e60125ed94496421801)

- **作者**: LiJzd
- **时间**: 2026-07-06T13:33:05Z
- **提交信息**: [Doc] Clarify fastokens availability (#45813)

Signed-off-by: LjjJzd <3542531707@qq.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [07f9baf](https://github.com/vllm-project/vllm/commit/07f9baf7564b42ba7218ce9167bfcc4128028473)

- **作者**: Kunshang Ji
- **时间**: 2026-07-06T13:18:33Z
- **提交信息**: Revert "[Platform] Replace `torch.cuda.Event` with `torch.Event` (#47140)" (#47668)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [7a90eb9](https://github.com/vllm-project/vllm/commit/7a90eb98ab70dcca8360214eb3cc08c999137861)

- **作者**: Ayushman Singh
- **时间**: 2026-07-06T13:04:00Z
- **提交信息**: [Bugfix] [Gemma4] Fix Gemma4 MTP draft model layers ignoring quant_config (#47091)

Signed-off-by: Ayushman Singh <40520701+ayush1399@users.noreply.github.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [8f4c69b](https://github.com/vllm-project/vllm/commit/8f4c69b22293424690ea5956d536c20c3d4ec393)

- **作者**: Bugen Zhao
- **时间**: 2026-07-06T13:02:59Z
- **提交信息**: [Rust Frontend] Cache metric handles for scheduler & request stats (#47444)

Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [8b79971](https://github.com/vllm-project/vllm/commit/8b79971bb9f97ca0dd59203c628f52de4664de10)

- **作者**: Artur Fierka
- **时间**: 2026-07-06T13:01:21Z
- **提交信息**: attention: pass None for unused args in unified attention TD path (#43597)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: quinnlp <quinnlp@users.noreply.github.com>

### [f676808](https://github.com/vllm-project/vllm/commit/f676808ba005f7d042d0db967f8dbe19a29c4b09)

- **作者**: Nick Hill
- **时间**: 2026-07-06T12:50:29Z
- **提交信息**: [CI] Use TTY for AMD CI tests for colored buildkite logs (#47730)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [98e4726](https://github.com/vllm-project/vllm/commit/98e4726a147f37666e1e9adc468e673b32373e21)

- **作者**: Qiming Zhang
- **时间**: 2026-07-06T12:45:48Z
- **提交信息**: [fix][run_batch]: respect proxy env vars when downloading media URLs (#47697)

Signed-off-by: mauyuyuace <qiming1.zhang@intel.com>

### [740f379](https://github.com/vllm-project/vllm/commit/740f379faefd1ddeb47c85ebd600af3ccae77b7a)

- **作者**: BadrBasowid
- **时间**: 2026-07-06T12:16:32Z
- **提交信息**: [ROCm][AITER] Directly Implement AITER Custom All-reduce in CudaCommunicator (#46065)

Signed-off-by: BadrBasowid <badr.basowid@gmail.com>

### [40cc2e8](https://github.com/vllm-project/vllm/commit/40cc2e83278f9280d80c2527fe03be1c5aa8c91f)

- **作者**: Alexis K.
- **时间**: 2026-07-06T11:56:23Z
- **提交信息**: [Bugfix] Return HTTP 422 for unprocessable image URLs instead of 500 (#47165)

Signed-off-by: Alexis Kinsella <alexis.kinsella@gmail.com>

### [ba22152](https://github.com/vllm-project/vllm/commit/ba22152096b2484faa3579624a253d54804d876d)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-07-06T09:36:49Z
- **提交信息**: fix(security): block request-level GPU video backend selection withou… (#47259)

Signed-off-by: jperezde <jperezde@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [90ce3a0](https://github.com/vllm-project/vllm/commit/90ce3a09bef2fd7203369b3f7aeabee15ea6f0f8)

- **作者**: Yan Ma
- **时间**: 2026-07-06T09:15:50Z
- **提交信息**: [bugfix] fix MOSS-Audio deepstack_input_embeds initialization in PP (#47607)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [26c754d](https://github.com/vllm-project/vllm/commit/26c754d8475e753928d57b71c2398515eabe0a0d)

- **作者**: Ma Jian
- **时间**: 2026-07-06T09:15:26Z
- **提交信息**: [XPU][Bugfix] Do not transpose weight_scale_inv at load time (#47116)

Signed-off-by: Ma Jian <jian1.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [3d7f357](https://github.com/vllm-project/vllm/commit/3d7f357ebf4db408b71786b517aaca6db21f6bde)

- **作者**: Sungjae Lee
- **时间**: 2026-07-06T09:01:10Z
- **提交信息**: [Doc] docs: fix note formatting for pooling models (#47701)

Signed-off-by: Sungjae Lee <33976427+llsj14@users.noreply.github.com>
Signed-off-by: Sungjae Lee <sung-jae.lee@navercorp.com>

### [736f1a5](https://github.com/vllm-project/vllm/commit/736f1a590714d4f1286fcc764439ad39cca2e8f5)

- **作者**: liuzhenwei
- **时间**: 2026-07-06T08:52:44Z
- **提交信息**: [XPU] Route mm_prefix models to Triton attention backend (#47688)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [344609a](https://github.com/vllm-project/vllm/commit/344609ab170a040fe5cfec74eac8db66cd344b6f)

- **作者**: Li, Jiang
- **时间**: 2026-07-06T08:24:24Z
- **提交信息**: [CI/Build] Fix pre-commit check (#47695)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [d039c17](https://github.com/vllm-project/vllm/commit/d039c171144bdc6e19d14d3dd9b0625f84f16d1c)

- **作者**: xiaozhoupy
- **时间**: 2026-07-06T08:07:56Z
- **提交信息**: [Bugfix] Recycle post-final-norm hidden in GLM MTP (single norm) (#47448)

### [cdab283](https://github.com/vllm-project/vllm/commit/cdab28319f5ea9521f93a31c7e5f14e4d2c194be)

- **作者**: xiangdong
- **时间**: 2026-07-06T07:15:45Z
- **提交信息**: [XPU][CI]Add agent tags for Basic Models Tests (Initialization) in Intel GPU CI (#47675)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [2fa1056](https://github.com/vllm-project/vllm/commit/2fa10566e3b9a50e56e6464a3469091b073ab592)

- **作者**: Qiming Zhang
- **时间**: 2026-07-06T07:09:16Z
- **提交信息**: [Core][DP] Rotate load-balancer tie-break to avoid systematic engine bias (#47420)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>

### [fb265fc](https://github.com/vllm-project/vllm/commit/fb265fc8fb4e35b5160938bb2ad909be0e0ab4d3)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-06T07:06:16Z
- **提交信息**: [ROCm][CI] Increasing parallelism in Basic Models Tests (Extra Initialization) (#47591)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [8f0e75e](https://github.com/vllm-project/vllm/commit/8f0e75e16b96e07ae58283e440128b491f729972)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-06T07:04:58Z
- **提交信息**: [ROCm][CI] Adding nixl multiconn (#47481)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-07
**监控日期**: 2026-07-06
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5460
- **最后更新**: 2026-07-06T20:18:00Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: herotai214, amy-why-3459, Vensen

## AI分析总结

根据提供的提交记录，以下是昨日更新的要点总结，结合 vllm-omni 项目（致力于**简易、快速、低成本的通用多模态模型服务**）的背景进行分析：

---

### 1. 主要更新类型
- **全部为 Bug 修复（Bugfix）**，无新增功能、性能优化或重构。

### 2. 关键变更点及其与项目方向的关系
| 提交 | 关键变更 | 与项目方向的关系 |
|------|----------|------------------|
| `#4918` | 修复 `higgs-audio-v3` 测试中 tokenizer config 的错误 | 直接提升音频模态（Audio）的兼容性，支撑“omni-modality”（全模态）的易用性目标 |
| `#4910` | 修复全负载（full-payload）多模态拆分在双隐藏/调度批次轴下的 bug（#4870 的后续） | 优化多模态数据在复杂批次结构下的正确性，确保“fast”与“cheap”背后调度逻辑的可靠性 |
| `#4912` | 修复睡眠模式（sleep mode）pytest CI 错误 | 保障持续集成稳定性，间接提升项目维护效率与迭代速度 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：修复音频模型的多模态测试问题，减少用户在使用 “omni-modality” 服务时遇到的配置错误。
- **批处理可靠性**：针对双批次轴的多模态拆分修复，保障了高并发或复杂调度场景下的正确性，契合“fast”与“cheap”所需的吞吐优化基础。
- **CI 健壮性**：睡眠模式下的 pytest 修复确保自动化测试不会因环境问题而误报，有利于长期迭代。

### 4. 值得关注的技术点
- **双批次轴（dual hidden/scheduled batch axes）**：暗示 vllm-omni 可能内部同时维护隐藏态与调度维度的批次轴，多模态拆分需同时考虑这两个维度，这是一个较为复杂的张量操作修复。
- **tokenizer config 与音频模型**：`higgs-audio-v3` 是音频层模型，其 tokenizer 配置修复说明项目正拓展对非文本模态（音频）的精细支持。

### 5. 对项目发展的影响（结合 README 目标）
- vllm-omni 的 slogan 强调 **Easy, fast, cheap** 和 **omni-modality**。这些 bug 修复虽然小，但直接消除潜在的用户体验障碍（配置错误）和服务正确性隐患（批量拆分错误），符合“Easy”和“cheap”的稳定基础要求。
- 修复多模态拆分与 CI 流程，为后续引入更多模态（视频、图像等）以及更高效调度策略铺平道路，推动“omni-modality”从实验走向生产可用。

## 详细提交记录

### [d4a869f](https://github.com/vllm-project/vllm-omni/commit/d4a869fe5e2edd49af48026051948c8d1018d727)

- **作者**: herotai214
- **时间**: 2026-07-06T10:53:24Z
- **提交信息**: [Bugfix] Fix tokenizer config for higgs-audio-v3 test error (#4918)

Signed-off-by: herotai214 <herotai214@gmail.com>

### [9ceca4e](https://github.com/vllm-project/vllm-omni/commit/9ceca4ec85c21d1806ea69d74002e0f9e96bbca7)

- **作者**: amy-why-3459
- **时间**: 2026-07-06T07:08:05Z
- **提交信息**: [Bugfix] Fix full-payload mm splitting for dual hidden/scheduled batch axes (#4870 follow-up) (#4910)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [ba7e9e6](https://github.com/vllm-project/vllm-omni/commit/ba7e9e64960a86d2d40b0dd014fe101414c96d01)

- **作者**: Vensen
- **时间**: 2026-07-06T07:07:01Z
- **提交信息**: [CI][sleep mode] fix sleep pytest CI error (#4912)

Signed-off-by: vensen <vensenmu@gmail.com>

---
