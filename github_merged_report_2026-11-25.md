# GitHub Stars 合并报告 - 2026-11-25

**合并日期**: 2026-11-26
**监控日期**: 2026-11-25
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


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2304
- **最后更新**: 2026-11-25T20:49:27Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: NancyFyong, Coach257, Albert Zhang

## AI分析总结

# VeOmni 昨日提交分析

## 1. 主要更新类型

本次 5 条提交以**性能优化**和**功能新增**为主，辅以少量 Bug 修复与文档更新。其中 2 条涉及分布式训练与检查点加载（性能/功能）、1 条涉及 FP8 量化算子（性能）、1 条涉及混合精度修复（Bug）、1 条为文档修正。

## 2. 关键变更点及与项目方向的关系

- **分布式 FQN 排序修复**（29e65b2）：修复了完全限定名排序时后代未先于祖先的问题，属于分布式参数管理的正确性修复，直接支撑"Model-Centric Distributed"的核心定位。
- **DeepGEMM FP8 算子接入**（4fe0c52）：将 DeepGEMM 的 FP8 行式计算引入 dense linear 与 gated_mlp 系列算子，是对大规模训练中低精度高性能算力路径的持续扩展，与项目"Scaling"的目标高度一致。
- **检查点与流式加载增强**（3ea32fb）：新增 `extra_parallel_only`、行式伴随流式加载与延迟 HF 分片合并，优化了大规模模型检查点的加载效率与灵活性，是分布式训练基础设施的重要补强。
- **H3 混合精度 FP32 投影修复**（c394b01）：确保 H3 官方 FP32 投影在混合精度下不被错误降精度，属于数值稳定性保障。
- **文档修复**（4254f03）：修复 Quay 镜像链接并更新昇腾镜像示例，提升跨平台（含 Ascend）的部署可用性。

## 3. 对项目的影响和潜在意义

这批提交整体上**加固了分布式训练底座**，同时**拓宽了低精度算子生态**。FQN 排序与混合精度修复提升了训练正确性与数值可靠性；DeepGEMM FP8 接入为大模型训练带来实际吞吐收益；检查点流式加载则降低了大规模模型重启与迁移的门槛。三者共同指向 VeOmni "让任意模态模型训练可扩展"的愿景，使分布式配方库在性能、正确性与易用性上同步演进。

## 4. 值得关注的技术点

- **DeepGEMM FP8 行式 GEMM** 在 dense linear 与 gated_mlp 上的落地方式，以及与现有量化路径的兼容策略。
- **rowwise companion streaming load** 的设计——如何在流式加载中保持行式布局与检查点一致性。
- **deferred HF shard merge** 的延迟合并机制，对超大模型分片加载的内存与延迟优化。
- FQN 排序中"后代先于祖先"的拓扑约束，反映分布式参数树的遍历语义。

## 5. 对项目发展的影响

结合 README 中"Model-Centric Distributed Recipe Zoo"的定位，这批提交表明项目正从"搭建分布式训练框架"迈向**"打磨生产级可靠性与性能"**的阶段：一方面通过 FP8 算子与流式加载持续压榨大规模训练的性能上限，另一方面通过多处正确性修复夯实数值与拓扑基础。文档对 Ascend 镜像的更新也暗示项目在**多硬件生态（含国产加速卡）**上的布局意图。整体来看，这些改动将提升 VeOmni 在真实大规模、多模态训练场景中的可用性与竞争力，为其论文与开源社区采用提供更坚实的工程支撑。

## 详细提交记录

### [29e65b2](https://github.com/ByteDance-Seed/VeOmni/commit/29e65b28efd4e2abc9aebb2771226e2f0277ef85)

- **作者**: Coach257
- **时间**: 2026-11-25T07:47:49Z
- **提交信息**: [dist] fix: sort descendants before ancestors in FQN sort (#1498)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [c394b01](https://github.com/ByteDance-Seed/VeOmni/commit/c394b0121fbd26a8595b945d7b294d570bc8f6af)

- **作者**: NancyFyong
- **时间**: 2026-11-25T07:34:49Z
- **提交信息**: [model, docs] fix: keep H3 official FP32 projections under mixed precision (#1260)

### [4fe0c52](https://github.com/ByteDance-Seed/VeOmni/commit/4fe0c52ea387b7a01011b11dd470d844b501ba20)

- **作者**: Coach257
- **时间**: 2026-11-25T07:26:33Z
- **提交信息**: [ops, model] feat: add DeepGEMM FP8 rows on the dense linear and gated_mlp families (#1492)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [3ea32fb](https://github.com/ByteDance-Seed/VeOmni/commit/3ea32fbad7986f4455e5b65853361f3be49bac24)

- **作者**: Coach257
- **时间**: 2026-11-25T06:29:49Z
- **提交信息**: [ckpt, dist, omni] feat: support extra_parallel_only, rowwise companion streaming load, and deferred HF shard merge (#1450)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [4254f03](https://github.com/ByteDance-Seed/VeOmni/commit/4254f03b6059e1a1c746ddffb9d45b927ac0367e)

- **作者**: Albert Zhang
- **时间**: 2026-11-25T03:11:53Z
- **提交信息**: [docs] fix: repair Quay links and refresh Ascend image examples (#1499)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3027
- **最后更新**: 2026-11-26T03:12:51Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Shiqiao Gu (谷石桥)

## AI分析总结

## LightX2V 仓库昨日提交分析

### 1. 主要更新类型
- **文档更新**：README 描述增强，突出多模态能力和性能特性
- **功能新增**：训练模块中添加 MiniMax-H3 蒸馏最佳实践指南

### 2. 关键变更点及与项目方向的关系
- README 描述扩展了 LightX2V 的定位，从单纯的推理加速框架扩展到强调**多模态能力**，这与当前视频生成领域从单模态向多模态（如文本、图像、视频联合生成）演进的趋势一致，有助于明确项目在开源社区中的差异化定位。
- MiniMax-H3 蒸馏最佳实践的添加，属于**训练侧的能力建设**。蒸馏是实现轻量化推理的关键手段，与 LightX2V 以"轻量高效"为核心的目标直接契合。提供最佳实践文档/配置，能降低开发者使用门槛，促进生态采用。

### 3. 对项目的影响和潜在意义
- README 更新面向潜在用户和贡献者，**提升项目可见性和认知度**，是开源项目运营的常规但重要动作，有助于吸引更多模型厂商和用户参与。
- 蒸馏最佳实践的加入表明项目正在从单一模型支持向**多模型、多厂商生态覆盖**扩展（此前已支持多种视频生成模型），增强了框架的通用性和工业落地能力。同时也说明团队在持续完善训练工具链，为下游社区复现和定制模型提供支持。

### 4. 值得关注的技术点
- **蒸馏策略**：MiniMax-H3 蒸馏的具体方法（如特征蒸馏、步数蒸馏或对抗蒸馏）值得深入关注，这关系到在保持生成质量的前提下能将推理步数压缩到何种程度。
- **多模态描述扩展**：README 中新增的多模态描述暗示项目可能已或将要支持更丰富的输入模态（如图像条件、音频同步等），这对理解项目技术路线图有参考价值。
- **最佳实践的工程化程度**：以"最佳实践"形式提供而非硬编码，说明项目倾向于以灵活配置支持社区定制，符合开源项目的可扩展性设计理念。

### 5. 对项目发展的影响（基于README背景）
LightX2V 作为面向轻量级视频生成加速的开源框架（Apache 2.0 协议、提供中英文文档和 Docker 支持），这两笔提交分别从**品牌传播**和**技术纵深**两个维度推动项目发展。README 的更新强化了项目作为多模态视频生成加速方案的市场定位；蒸馏最佳实践的贡献则夯实了训练侧的技术底座，使 LightX2V 不仅是推理加速器，更成为覆盖"训练-蒸馏-推理"全链路的轻量化解决方案。两者结合，有助于项目在竞争激烈的视频生成开源生态中建立更完整的技术叙事和更广泛的用户基础。

## 详细提交记录

### [83a424a](https://github.com/ModelTC/LightX2V/commit/83a424ac3c60849601ee7b6c393cae53a49f843c)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-11-25T07:07:54Z
- **提交信息**: Enhance LightX2V description in README (#1757)

Expanded description of LightX2V to include multimodal capabilities and
performance features.

### [7fc25cd](https://github.com/ModelTC/LightX2V/commit/7fc25cddd61ffbace4e9be98e64618822468ba4a)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-11-25T06:41:54Z
- **提交信息**: feat(train): add MiniMax-H3 distillation best practices (#1730)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2345
- **最后更新**: 2026-11-24T14:56:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 7007
- **最后更新**: 2026-11-26T02:00:02Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 7
- **主要提交者**: Jimmy Zhou, Perkz Zheng, Yuxian Qiu

## AI分析总结

# FlashInfer 昨日提交综合分析

## 主要更新

昨日 11 个提交可归为四类：**性能优化**（3 项：稀疏 MLA、MoE epilogue、CuTe DSL 编译并行化）、**CI/基础设施**（5 项：PR 测试流程重构、H100 节点恢复、NCCL 版本修复、`cuda-core` 依赖约束修复、Docker 镜像标签更新）、**Bug 修复与测试**（2 项：FP8 all-reduce 测试参考值、head-major 输入弃用处理）、**版本发布**（1 项：bump 至 0.7.6）。

## 关键变更

**推理内核性能**：稀疏 MLA 改用完整 cluster grid，GB300 上 decode 从 53.40 降至 31.69 µs，提升近 40%；MoE pre-FC2 GEMM1 epilogue 通过紧凑 decode tile 与打包 BF16 舍入消除 ALU 瓶颈，且输出保持逐位一致；CuTe DSL 编译支持多进程并行与文件锁去重，缓解编译延迟对推理启动的影响。

**API 兼容治理与发布**：0.7.6 版本附带完整 API 差异审计——移除 163 个 CAKE 训练函数、新增 6 个，显示项目正聚焦推理、剥离训练代码。`decode_cp_a2a_lse_reduce` 在布局破坏性变更后补充 `layout` 参数与弃用警告，为 head-major 调用方提供两个 minor 版本过渡期，体现对 vLLM 等下游生态的兼容承诺。

**工程与 CI 可靠性**：PR 测试重构为可复用 workflow（`pr-test.yml` 加 dispatch 拆分）以修复 self-hosted runner 排队问题；恢复 H100 测试节点；修复 EP 环境 NCCL 降级导致的符号缺失；动态 FP8 all-reduce 测试首次纳入多 GPU CI，暴露并修复了 9 个长期未被发现的失败用例。另将 CI 镜像中 `cuda-core` 约束收紧为 `<1.3`，因 1.3.x 对 CUDA Python bindings 有更高运行时门槛，导致 NVSHMEM 测试在收集阶段失败；同时例行更新镜像标签为 `20261124-98c130a`。

## 技术关注点

- **无行为变更的性能范式**：紧凑 decode tile 优化保持 FP4 输出逐位一致；`cvt.rn.bf16x2.f32` 打包舍入同时用于两条路径，减少半数转换指令。
- **JIT 部署细节**：CuTe DSL 编译缓存采用元数据标记校验、跨 worker 特化复用，并处理 `FLASHINFER_DISABLE_JIT=1` 下的冷 miss 报错。
- **测试精度诊断**：FP8 量化张量比较时忽略单个 e4m3 码点即占 6.25%–12.5% 的值，修复精准对齐量化容差。
- **依赖约束策略**：选择 `cuda-core<1.3` 而非 `!=1.3.1`，因 1.3.0 同样不兼容，避免逐版本"打地鼠式"修复；已在隔离环境验证 `cuda-core==1.2.2` 兼容三种 bindings 版本并跑通 CPU 侧测试（29 通过）。
- **已知残余风险**：完整 Docker 镜像构建与 GPU 测试仍待运行，约束在全量镜像中的生效尚未完全验证。

## 项目影响

结合 README 的"高性能 GPU 推理内核"定位，本批提交显示项目处于 **GB300/SM100 架构深度优化与发布工程成熟化** 阶段。稀疏 MLA、NVFP4 MoE 等针对新硬件的优化直接兑现性能承诺；CI 重构、API 弃用策略、版本审计与多 GPU 测试纳入建立了支撑快速迭代的工程基线，将缩短 PR 验证周期、利于社区贡献流入。

同时也暴露改进空间：自动生成的 CI 镜像（由 `ci/cuda-versions.json` 驱动）可能引入不兼容依赖，与人工修复形成 #9334 → #10005 的追溯链，提示 release-ci-docker 工作流需增加依赖兼容性预检。总体而言，这些提交使项目在**性能领先性**与**生态稳定性**两维度同步前进，低风险、高必要性的基础设施维护虽不改变用户可见功能，却保障了核心质量验证管道的畅通，为 0.7.6 及后续版本的可靠发布奠定了基础。

## 详细提交记录

### [edefa08](https://github.com/flashinfer-ai/flashinfer/commit/edefa080987d1940b97fdb62e3cfc2f0b3ce4d2f)

- **作者**: Adrian
- **时间**: 2026-11-25T23:57:23Z
- **提交信息**: ci: run PR checks through the allowlisted main workflow (#10046)

<!-- .github/pull_request_template.md -->

## 📌 Description

PR test jobs run from a pull-request merge ref, while the runner-group
allowlist permits `pr-test.yml@refs/heads/main`. This leaves the
self-hosted checks queued, as seen on #10010.

Keep `pr-test.yml` as the reusable workflow that directly defines the
self-hosted test matrix and provider-spec lint. Move triggers,
authorization, setup, and reporting into `pr-test-dispatch.yml`, which
calls `flashinfer-ai/flashinfer/.github/workflows/pr-test.yml@main` with
the selected source and matrices. The existing runner allowlist remains
unchanged.

The reusable workflow independently authorizes the original event and
verifies the selected source before either runner job starts. Manual
dispatches outside `main` fail before setup. Both runner jobs remove
only containers mounted to their exact checkout.

Reusing a prior pass requires a recorded match for PR head, current base
and merge tree, including ordinary full runs and partial reruns. Legacy
or expired source records require fresh CI. History refreshes every five
minutes and backs off on API failures; unreadable history stays unknown.

Update scope evidence, workflow references, and nested job reporting.
Preserve secrets, matrix fail-fast behavior and snapshot verification.
Use the supported `github.workspace` context for the compile-cache
directory.

## 🔍 Related Issues

Related: #10010 (runner scheduling investigation).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file pre-commit hooks passed, including the commit hooks. The
full repository hook suite was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Local workflow and CPU infrastructure checks cover this
refactor; live runner admission requires the reusable interface to reach
`main`.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/infra
tests/cpu/jit/test_jit_spec_gencode_lint.py tests/infra/test_sharding`

Validation:

- actionlint passed for the reusable workflow, dispatcher, and cleanup
workflow, with the organization’s custom runner labels configured;
optional shellcheck was disabled.
- 116 focused CPU tests passed; workflow-only validation without `jq`:
46 passed and 6 skipped.
- Broader bot-scope and workflow tests: 67 passed, 119 subtests passed.
Excluded one existing capitalization assertion
(`test_target_explanations_are_sanitized_but_commands_remain_copyable`),
previously reproduced on unchanged base code.
- Standards and spec reviews found no remaining code findings after
fixing source inheritance for partial reruns.
- Targeted-lane scope selftest and `git diff --check` passed.

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

Deployment requires the reusable `workflow_call` interface on `main`
before the dispatcher invokes it. The required `Test Results Summary`
check blocks ordinary pre-merge validation of the pinned call until that
prerequisite is met. Stage the reusable interface first, or obtain an
authorized cutover exception; this rollout finding remains open. Live
runner verification follows deployment. Manual dispatches and
workflow-specific API queries now use `pr-test-dispatch.yml`. The `PR
Test` workflow name and required `Test Results Summary` name remain
unchanged.

Implemented with AI assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **CI Improvements**
* Pull request test runs require the `run-ci` or `run-ci-focused` label.
Focused runs verify the selected test scope against a published
snapshot.
* Scheduled test runs run three times daily. Failures are tracked
automatically, and tracking issues close after successful runs.
* Test results report lane outcomes and check for empty test lanes and
trace-coverage gaps. Documentation- or configuration-only changes can
skip builds.
* Test execution uses a dispatcher and reusable workflow, with checks
for authorized runs.
* **Documentation**
* Updated CI guidance to reflect the workflow split and pull request
testing process.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1ec9ad3](https://github.com/flashinfer-ai/flashinfer/commit/1ec9ad31183e2d4356f17b8ffeeb9994ab2752bc)

- **作者**: Perkz Zheng
- **时间**: 2026-11-25T19:08:27Z
- **提交信息**: perf(prims-ts): use full cluster grid for persistent sparse MLA (#9967)

## 📌 Description

Use the hardware cluster cap for persistent direct-sparse 2-CTA MLA.
Live rows can fill the first round of a padded batch.

## 🚀 Pull Request Checklist

- [x] Changed-file pre-commit checks passed.

## 🧪 Tests

- GB300, 128 heads, 2,048 selected KV entries, FP8 Q and NVFP4 KV with
FP8 RoPE. At 60 live rows in 100 slots, the grid grew from 50 to 76
clusters and decode fell from **53.40 to 31.69 µs**.
- Four sparse MLA graph tests passed. All 20 A/B workloads matched
bitwise.

## Reviewer Notes

AI-assisted implementation and validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* Persistent static-grid MLA decode launches now consistently use the
physical cluster limit, rather than scaling launch size to the amount of
live work.
* BF16 persistent launches size their CLC grid according to logical
work, which may exceed the physical cluster limit.
* Row buckets that select the same profile can reuse a compiled kernel.
* **Documentation**
* Clarified the launch-sizing differences and compiled-kernel reuse
behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: mingyangw <35635157+saltyminty@users.noreply.github.com>

### [f7610f6](https://github.com/flashinfer-ai/flashinfer/commit/f7610f64a30579f4ff8235dd847223a781ea31a6)

- **作者**: feih-nv
- **时间**: 2026-11-25T17:58:13Z
- **提交信息**: test(comm): fp32 reference and an FP8-step tolerance in the dynamic FP8 all-reduce test; run it in multi-GPU CI (#9950)

<!-- .github/pull_request_template.md -->

## 📌 Description

`tests/comm/test_trtllm_allreduce_dynamic_fp8_quant.py` fails 9 of its
18 cases on main on 4-GPU GB200 and GB300 nodes. The kernel is right;
the test's reference and tolerance are not. Multi-GPU CI never ran this
file, so the failures were not seen.

**Why the 9 cases fail**

- The reference summed the ranks and normalized in the input dtype. The
kernel (`fp32_acc=True`) sums in fp32 and rounds once. With 4 ranks the
two sums differ by up to 0.06; with 2 ranks the sums agree and only the
fp16 RMSNorm differs, by up to 0.004.
- The check compared two quantized tensors at 5%. One `float8_e4m3fn`
code is 6.25% to 12.5% of the value, so any element near a rounding
boundary that lands on the neighbouring code fails the test.
- Failing cases: all four 4-rank bf16 cases (2,300 to 4,100 of 65,536
elements), both `ws2_m1024` cases and three of the four `ws2_m128` cases
(19 to 105 of 1M to 4M elements).

**What**

- `_reference` follows the kernel's order: sum the ranks in fp32, round
once to the input dtype, add the residual in that dtype, RMSNorm in
fp32.
- The dequantized output is compared with the unquantized reference,
within FP8 rounding: half an e4m3 step at the value's magnitude, plus
0.1 step for the kernel's intermediate rounding.
- The file is added to `SPAWN_MANAGED_TEST_FILES`.

No kernel change. The residual check and the scale tolerances are
unchanged. The scale reference is now computed from the fp32 RMSNorm
output instead of the input-dtype one, a difference far below its
`atol=1e-3`.

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
`tests/comm/test_trtllm_allreduce_dynamic_fp8_quant.py`

4-GPU nodes, CI container (CUDA 13.0),
`tests/comm/test_trtllm_allreduce_dynamic_fp8_quant.py`:

| | GB200 | GB300 |
|---|---|---|
| main (`560d7e296`) | 9 passed, 9 failed | 9 passed, 9 failed |
| this PR | 18 passed | 18 passed |

Evidence that the kernel is right (diagnostic on GB200, main): in the
cases with a norm output, the kernel's FP8 output equals the
quantization of its own norm output exactly. With this PR's reference,
every element of all 18 cases is within 0.6 e4m3 step.

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

- An fp32 reference that adds the residual in fp32 (skipping the
rounding of the sum to the input dtype) fails the residual cases by more
than ten FP8 steps on elements where sum and residual nearly cancel. The
kernel rounds the sum first; the reference now does too.
- #9949 appends another file to the same `SPAWN_MANAGED_TEST_FILES`
line; whichever lands second needs a trivial rebase.
- Known flake, not from this change: `multi_gpu_test_gb200: [cu129]` on
this PR had 17 passed and 1 failed with `EADDRINUSE` when rank 0 opened
its TCPStore. `_get_open_port` (already on main, and in about ten other
comm test files) binds a free port, releases it and hands the number to
the ranks, so another process can take it in between. The case passed in
the other multi-GPU jobs and in the four cluster runs above. A re-run
clears it; a retry on a fresh port would remove it and can be added here
if wanted.
- The 0.6-step bound is tighter in meaning than the old 5% on large
values and looser on small ones, where one code is up to 12.5%.

### [ae93aae](https://github.com/flashinfer-ai/flashinfer/commit/ae93aaed3d19c9c309dcea0c0d9026e9e53baf76)

- **作者**: amitz-nv
- **时间**: 2026-11-25T17:23:53Z
- **提交信息**: perf(moe): faster pre-FC2 GEMM1 epilogue (compact decode tiles, packed BF16 rounding) (#9848)

## 📌 Description

In the routed NVFP4 MoE path that applies the routing weights before FC2
(pre-FC2, #9260), the gather GEMM1 epilogue (BF16-rounded ClampedReLU2,
route weight, NVFP4 quantization of the FC2 input) is the per-tile
bottleneck of GEMM1:

- A GEMM1 tile costs a constant ≈5.4 µs at every M on GB300, whether 2
or 128 of its 128 rows hold routes, while GEMM2 streams the same weight
bytes per expert at ≈3.5 µs per tile. GEMM1 runs at 3.07 TB/s, GEMM2 at
6.43 TB/s (ncu, M=96).
- The epilogue is ALU/XU-bound: every epilogue warp sends its 32 TMEM
rows × 128 columns through four single BF16 roundings (`F2F.BF16` +
shifts), `tanh.approx` and `div.full`, for all 128 rows of the tile,
including padding rows. `F2F.BF16` and `SHF` lead the epilogue stall
samples.

This PR makes that epilogue cheaper. There is no new argument or
setting: it applies whenever the gather GEMM1 gets `routing_weights`
(`routing_weights_before_fc2=True` in the CuTe-DSL fused MoE APIs).

- **Compact decode tiles:** a tile with at most 64 valid rows stages
`bf16(alpha * acc)` of its valid rows in the `sC` buffers; all 128
epilogue threads then quantize one 16-column block each and store the
FP4 bytes and the scale byte directly. Padding rows are not processed.
Tiles with more valid rows keep the per-subtile path.
- **Packed BF16 rounding:** one `cvt.rn.bf16x2.f32` per pair of
roundings, in both paths.

**Behavior:** the same per-element operations in the same order, so the
FP4 output and the scale factors of every valid row are bitwise
identical to before. Padding rows of `out` / `out_scale` (rows of a tile
past its `tile_idx_to_mn_limit`) may now be left unwritten; GEMM2 never
stores padding rows. Kernels without `routing_weights` are unchanged:
identical PTX and cubin to `main` for ClampedReLU2 and gated SwiGLU
configurations (sm_103a). SM100/SM103 only, like the kernel.

**Performance** (GB300, one full MoE call — routing sort, GEMM1, GEMM2 —
in a CUDA graph, cold weights, µs, before → after, mean of two
alternating runs). Layer: 512 experts, top-10, hidden 1536, intermediate
7168, NVFP4 weights and activations; per GPU, 4-way TP = 512 experts ×
1792, 8-way TP = 512 experts × 896, 4-way EP = 128 experts × 7168;
uniform routing:

| M (tokens) | 4-way TP | 8-way TP | 4-way EP |
|---|---|---|---|
| 1 | 20.6 → 17.3 (1.19×) | 18.5 → 15.0 (1.23×) | 22.6 → 19.0 (1.19×) |
| 8 | 77.5 → 53.4 (1.45×) | 45.6 → 33.3 (1.37×) | 85.1 → 57.3 (1.49×) |
| 64 | 284.0 → 182.9 (1.55×) | 150.2 → 99.1 (1.52×) | 286.1 → 187.6
(1.52×) |
| 256 | 398.5 → 259.1 (1.54×) | 210.2 → 138.7 (1.52×) | 397.5 → 260.8
(1.52×) |
| 1024 | 406.1 → 268.1 (1.51×) | 214.6 → 144.5 (1.49×) | 403.7 → 267.5
(1.51×) |
| 4096 | 430.3 → 340.2 (1.26×) | 242.7 → 199.1 (1.22×) | 420.9 → 335.6
(1.25×) |
| 8192 | 722.5 → 528.4 (1.37×) | 440.9 → 354.1 (1.25×) | 709.2 → 503.3
(1.41×) |
| 16384 | 1095.5 → 827.6 (1.32×) | 678.8 → 549.2 (1.24×) | 1027.6 →
765.3 (1.34×) |
| 32768 | 1996.0 → 1505.1 (1.33×) | 1237.2 → 995.2 (1.24×) | 1831.7 →
1354.9 (1.35×) |

With skewed routing (expert popularity `exp(S·z)`, `z` standard normal,
S = 0.5 and 1.0) the speedup is 1.16×–1.54× over the same sizes. End to
end, in a vLLM serving benchmark of an NVFP4 MoE model (TP4, 128
concurrent sessions, speculative decoding), this epilogue raised output
throughput by 5.9%.

**Tests** (`tests/moe/test_routed_nvfp4.py`): the existing bitwise tests
against the separate reference quantizer now exercise both paths (17
tokens: compact tiles; 300 tokens: 75-row tiles; 270,000 tokens: full
tiles plus a compact tail tile stored past 2^31 bytes). New cases: tiles
of 32, 33, 64 and 65 valid rows around the compact threshold; one CTA
(`sm_count=1`) running full and compact tiles back to back; an
end-to-end and CUDA-graph replay case with 75-row tiles. The bitwise
tests prefill GEMM1's outputs with bytes no valid row can hold, so a
skipped store fails. Also checked on real layer weights against the
original epilogue: GEMM1's FP4 rows and scale bytes, matched per route,
and the MoE output are bitwise identical at 162 points (the three shards
above, 1 to 32768 tokens, uniform and skewed routing, plus all-zero
tokens, a few hot experts and large activations).

## 🔍 Related Issues

Builds on the pre-FC2 routed NVFP4 path (#9260).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The changed files pass the pinned `ruff format`, `ruff check` and
`mypy`; the full hook set was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

On GB300 (SM103): `tests/moe/test_routed_nvfp4.py` 166 passed;
`tests/moe/test_cute_dsl_fused_moe.py` and
`tests/moe/test_cute_dsl_moe_cache_key.py` 827 passed, 38 skipped.
Kernels without routing weights compile to the same PTX and cubin as
`main` (ClampedReLU2 and gated SwiGLU, sm_103a).

## Reviewer Notes

- The pre-FC2 kernel uses 168 registers per thread (the limit; no spills
or stack with the current ptxas). Compact tiles address the output from
a 64-bit base per tile, so outputs past 2^31 8-byte words are handled. A
toolchain update should re-run the bitwise tests.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for applying runtime routing weights before FC2 in the
supported NVFP4 activation path.
* Eligible tiles now use compact output, including workloads with a mix
of full and compact tiles. Compact output padding rows are not written.
* **Documentation**
* Clarified that padding rows in the output tensors may be left
unwritten for certain configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [af5a474](https://github.com/flashinfer-ai/flashinfer/commit/af5a474da924c79dfa216ec5adfad7a5ceb1a53c)

- **作者**: Adrian
- **时间**: 2026-11-25T12:55:07Z
- **提交信息**: ci: re-enable H100 test jobs (#9985)

<!-- .github/pull_request_template.md -->

## 📌 Description

re-enable H100 in GitHub CI after the infrastructure restored.

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

* **Chores**
* Scheduled and manually started test runs now enable the H100 test
matrix by default. Pull request runs continue to require the
`H100_ON_PRS` setting to be enabled before running H100 jobs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b37daec](https://github.com/flashinfer-ai/flashinfer/commit/b37daecc1adafd9cf210314bed570fa67f6b55da)

- **作者**: Yuxian Qiu
- **时间**: 2026-11-25T09:02:11Z
- **提交信息**: feat: parallelize CuTe DSL builds and defer sparse MLA compilation (#9395)

<!-- .github/pull_request_template.md -->

## 📌 Description

Separate processes can compile different CuTe DSL kernels concurrently.
Within a process, CuTe compiler entry is serialized to protect shared
compiler options. A per-kernel file lock deduplicates builds, and a
module lock protects invalidation and export. Cache hits verify the
identity of the published metadata marker across the object read,
including on read-only filesystems. Cache-filling workers use
`compile_and_persist(force=False)` to reuse a specialization published
by another worker while they wait. The default still forces a rebuild.
MoE callers that need an executable use `build_and_load()`. If a sibling
invalidates an export during a load, the caller can use its retained
kernel. A spec that previously exported without an engine can rebuild an
executable when JIT is enabled.

`BatchSparseMLADecodePagedTSWrapper.plan(compile=False)` resolves the
finalized specialization and workspace size, leaves `compiled=None`, and
allocates no launch tensors. A caller-provided workspace is still
validated. After planning, `is_kernel_cached()` checks the on-disk
object and metadata without loading or compiling it. Call `plan()` with
its default `compile=True` before `run()`.

With the persistent disk cache enabled, cacheable PrimTS MoE GEMMs honor
`FLASHINFER_DISABLE_JIT=1`. A warm hit loads normally. A cold miss
raises `MissingJITCacheError`, so deployments using that flag must
populate the cache first. The MoE autotuner can defer a missing-kernel
error until the first forward requiring that tactic.

PrimTS attention probes and executable plans share one source digest per
process and strict-key setting. Each probe still checks the on-disk
object and metadata, so it sees kernels published by other workers. On
`2b2da3572`, 176 targeted CPU tests and two B200 tests passed, including
a cold wrapper probe, compile and reload.

## 🔍 Related Issues

TensorRT-LLM uses these APIs to schedule missing warmup variants.
Steady-state sparse tensor-view reuse is tracked separately in #9767.
Both PRs target `main` and can be reviewed independently. [TensorRT-LLM
integration](https://github.com/NVIDIA/TensorRT-LLM/pull/22274)

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

On `a2ba1d5c1`, the eight CPU files from the maintainer’s scoped run
passed locally on Python 3.10.22 (223 tests). The two changed test files
also passed on Python 3.12 (109 tests). The three previously failing
cases were reproduced before the fix. The MXFP8 worker test now verifies
`compile_and_persist(force=False)`, and the thread-isolation test
catches `concurrent.futures.TimeoutError`.

On `72c8bbfab`, 164 targeted CPU tests passed, along with the targeted
B200 deferred-plan, executable launch, and D576 checks. With JIT
disabled, the shared build/load path tries the existing artifact and
raises `MissingJITCacheError` on a miss before requesting a build lock.
In a fresh unprivileged process on B200, a missing artifact in a
read-only CuTe cache produced that error and its cached sibling loaded
and ran with bitwise-correct output.

On `a1d5a1715`, 110 targeted CPU tests passed. The B200 sparse MLA
caller-workspace/eager test and the batch-invariant GEMM shared-object
launch test both passed.

Cold MoE tactic precompilation on one B200 with CuTe DSL 4.8.0 took a
median **20.889 s** on the merge base (`db2373490`) and **20.208 s** on
this change. Each revision ran in three fresh processes with empty
caches. The BF16 SwiGLU case used 64 tokens, hidden size 1024,
intermediate size 512, eight experts and top-2 routing. Four distinct
tactic pairs compiled and published eight FC1/FC2 kernels per run. All
outputs matched across revisions and passed the PyTorch reference. The
measurement covers tactic fan-out, compilation, publication and reload.
Input setup, tactic selection and routing are outside the timing.

On review-fix head `91225f625`, 106 CPU tests passed covering CuTe cache
concurrency, consistent generations, read-only hits, engine-less export,
and the batch-invariant JIT cache. The B200 sparse MLA workspace and
batch-invariant GEMM shared-object launch tests both passed.

All 86 CPU JIT cache tests passed, including concurrent compilation for
different kernels and single publication for duplicate requests. The
B200 caller-workspace test covered deferred planning, rejection of an
uncompiled run, and disk-cache misses and hits. The B200 dense CP graph
smoke test passed after the compile-path refactor. Changed-file
pre-commit checks passed.

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Targeted CI paths: `tests/cpu/jit/test_cute_dsl_cache.py`
`tests/attention/test_attention_ts_sparse_mla.py`
`tests/attention/test_attention_ts_mla_cp.py`

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

## Downstream measurements of the combined integration

DeepSeek-V4-Flash ran on four B200s with TP4/EP4, attention data
parallelism, and 256 input and output tokens. Warmup times below are
rank-0 wall time. These historical runs include the TensorRT-LLM
worker-pool changes and the combined FlashInfer feature series. They
predate this PR split. Each row group compares revisions from the same
allocation.

| PrimTS cache and comparison | Mode | First warmup | First PrimTS phase
|
|---|---|---:|---:|
| Cold, main-base `c9c07e04` → standalone pool `e9e140d7` | Eager |
418.2 → 195.1 s | Included in attention warmup on main |
| Warm, main-base `c9c07e04` → cache check `715858bac0` | Eager | 42.50
→ 42.95 s | 5.10 s with the cache check |
| Same warm comparison | CUDA graph | 48.00 → 47.30 s | 5.15 s with the
cache check |

On a cold PrimTS cache, grouping all 12 specializations in one pool
saved **223.1 s** in the first warmup (one process per version). In the
warm comparison, the earlier standalone pool without the cache check
took **20.2 s eager / 20.0 s graph** in its first PrimTS phase on the
same node (one reference process per mode). Querying disk membership
saved about **15 s** in that phase. Main and the cache-check version
each ran in two fresh processes per mode.

The final implementation checks the cache again when the executor binds
its serving resources. We isolated this change on a separate exclusive
four-B200 node with the same FlashInfer code, comparing `715858bac0`
against its flag-removal patch, subsequently committed as `3fcfb3f572`.

| Final pass, warm disk cache | First-pass-only policy | Check every
pass (TRT-LLM) |
|---|---:|---:|
| Eager PrimTS phase / total final warmup | 0.85 / 5.65 s | 3.15 / 6.45
s |
| CUDA-graph PrimTS phase / total final warmup | 2.60 / 16.35 s | 3.55 /
16.65 s |

Both versions launched **zero workers** with all 12 exports available
and four workers enabled per rank. The additional 12 checks took **1.35
s** in a separate two-pass probe. The full PrimTS phase also includes
local planning and rank synchronization. If two new variants first
appear on the final pass, the new policy can compile them in parallel.

<details>
<summary>Steady-state time per output token</summary>

| Execution | Main-base → cache check, ms/token | First-pass-only →
every pass, ms/token |
|---|---:|---:|
| Eager C8 | 116.728 → 117.878 | 113.246 → 113.072 |
| Eager C128 | 121.362 → 121.814 | 117.265 → 117.218 |
| CUDA graph C8 | 7.755 → 7.842 | 7.346 → 7.345 |
| CUDA graph C128 | 11.913 → 12.454 | 11.685 → 11.697 |

Columns are separate experiments. Each used before/after/after/before
process order, two warmup batches and three measured batches per
concurrency in each process. In the main-base comparison, eager paired
differences changed sign with run order. Graph C128 averaged 4.5% slower
and included one 14.33 ms/token candidate batch. In the isolated flag
comparison the largest absolute difference was 0.174 ms/token. Outputs,
graph replay and KV capacity matched within each mode. Weight-file page
cache and weight-loading times varied across fresh processes.

</details>

## Reviewer Notes

Please check lock ordering, the cache recheck before compilation, and
whether the disk probe and executable plan identify the same artifact.

Prepared with AI assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Sparse MLA planning can defer compilation, check whether a planned
kernel is cached, and compile it later. Running a deferred plan before
compilation now raises an error.
* Added a check for whether an attention kernel is available in the
compilation cache.
* **Improvements**
* Builds for different kernels can proceed concurrently, while builds
for the same kernel remain serialized.
* Valid cached artifacts are preferred, with compiled kernels available
as a fallback when no valid artifact can be loaded.
* Cache loading validates artifacts and accounts for the current device.
Unsupported cache keys can still proceed with compilation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>

### [5564387](https://github.com/flashinfer-ai/flashinfer/commit/556438772364c8506e4b76c72b1227a0f7af69b9)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-25T04:20:50Z
- **提交信息**: fix(comm): deprecate head-major decode_cp_a2a_lse_reduce inputs instead of misreading them (#10013)

## 📌 Description

#6483 changed `decode_cp_a2a_lse_reduce` from head-major inputs
(`partial_o` `[..., heads, cp_size, head_dim]`, `partial_lse` `[...,
heads, cp_size]`, the contract since v0.7.1) to destination-major inputs
(`[..., cp_size, heads, head_dim]`, `[..., cp_size, heads]`).

A head-major caller usually gets a shape error, because the kernel
checks that the third-to-last dimension equals `cp_size`. When `heads ==
cp_size` (for example 8 local heads with DCP=8), the head-major layout
passes every check: the kernel reads the head axis as the destination
axis, and the output has the right shape and wrong values.

This PR keeps destination-major as the contract of
`decode_cp_a2a_lse_reduce` and gives head-major callers a deprecation
period instead of a silent change:

- New keyword-only `layout: Literal["dst_major", "head_major"] | None =
None`.
- `layout=None` infers the order from which axis has length `cp_size`:
  - only dim -3 → destination-major, unchanged from #6483;
  - only dim -2 (or a 2-D `[cp_size, head_dim]` input) → head-major;
- both (`heads == cp_size > 1`) → `ValueError` asking for `layout=`.
This is the case that was silent.
- Head-major inputs are copied into destination-major order and raise a
`DeprecationWarning`. Head-major support is removed after two minor
releases (v0.7.8); `decode_cp_a2a_lse_reduce` then serves
destination-major inputs only.

The kernel and C++ are untouched; destination-major calls run exactly as
in #6483.

Callers written against #6483 (for example vllm-project/vllm#69006) need
no change, except with `heads == cp_size`, where they pass
`layout="dst_major"`.

## 🔍 Related Issues

Follow-up to #6483 and #4929.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Hooks ran on commit (ruff, ruff format, mypy, whitespace): all
pass.

## 🧪 Tests

- [x] Tests added or updated:
- `test_layout_needs_to_be_resolvable` (no GPU needed): `heads ==
cp_size` with `layout=None` raises, and an unknown `layout` raises.
- `test_head_major_layout_matches_destination_major`: with 2 heads
(inferred) and with `heads == cp_size` (explicit `layout=`), head-major
input gives the destination-major result and warns; both LSE modes.
- Existing multi-rank tests and the benchmark pass `layout="dst_major"`,
so they keep running on a 2-rank lane where their 2 heads equal
`cp_size`.
- [x] `torchrun --nproc-per-node=4 -m pytest
tests/comm/test_dcp_lse_reduce.py` on 4-GPU NVLink nodes: 54 passed on
every rank, none skipped, on SM107 (4× GR100) and SM103 (4× GB300).
- [x] Scoped CI on `tests/comm/test_dcp_lse_reduce.py`: GitHub pass;
internal multi-GPU and multi-node lanes (B200, GB200, GB300, VR NVL72)
pass.

## ⚡ Performance

4 ranks, 2 heads per destination, head_dim 512, BF16, batch 1 to 64;
this PR vs `main` on the same node, eager (100 back-to-back calls) and
CUDA-graph replay, interleaved over 3 rounds:

| Input | SM107 (4× GR100) | SM103 (4× GB300) |
|---|---|---|
| Destination-major, `layout` inferred | 0.99x–1.01x | 0.98x–1.01x
eager, 1.00x graph |
| Destination-major, `layout="dst_major"` | 0.99x–1.01x | 0.99x–1.01x |
| Head-major (deprecated copy path), relative to destination-major |
0.57x–0.82x eager, 0.78x–0.85x graph | 0.36x–0.39x eager, 0.81x–0.84x
graph |

- Destination-major calls run at `main` speed. The second commit reads
`partial_o.shape` once during inference; before it, inferred calls on
the Grace host were 0.91x of `main` at batch 1 (eager only, from
per-call `dim()`/`size()` round trips).
- The head-major cost is the two transpose copies plus their launch
overhead, largest at small batch and in eager mode. Callers remove it by
passing destination-major inputs.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a layout option for reduction inputs, supporting
destination-major and head-major ordering. Layout can be inferred when
unambiguous; inputs with ambiguous dimensions require an explicit
choice.
* **Deprecation**
* Head-major input ordering remains supported but now emits a
deprecation warning.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5228ea6](https://github.com/flashinfer-ai/flashinfer/commit/5228ea6be8ec42a5abd656a9f89cad75d505389e)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-25T01:53:59Z
- **提交信息**: bump version to 0.7.6 (#9788)

<!-- .github/pull_request_template.md -->

## 📌 Description

Bump version to 0.7.6 for release. This PR changes only `version.txt`.
It stays a draft until `release-v0.7.6` is cut from main and `v0.7.6rc1`
is tagged; then it moves main to 0.7.6 so nightlies sort above 0.7.5.

## 🔍 Related Issues


https://github.com/flashinfer-ai/flashinfer/issues?q=is%3Aopen+label%3Av0.7.6

## Reviewer Notes

**API changes review**

API changes since `v0.7.5`, from `scripts/list_apis.sh` at main
`d91cc6c70`:

- **Removed:** 163 functions, all CAKE training entry points removed by
#9326. The release notes will announce the removal and point to the
migration path. The diff below lists each one as a single `def` line, so
the body stays under GitHub's size limit. Every other hunk is the
unchanged `-U0` output.
- **Added:** 6 functions: `localize_gdn_decode_state`,
`split_fp4_moe_weights_by_locality_domain`, `mm_mxfp8_mxfp4`,
`gather_nvfp4_kv_cache_by_position`, `compact_nvfp4_kv_cache` and
`qsa_sparse_paged_attention`.
- **Changed defaults:** `bsa_attn_sm100_blk64_fwd` now defaults
`backend` to `"auto"` (was `"cute"`), and `prepare_bgmv_moe` now
defaults `fallback` to `None` (was `True`).
- **Other signature changes:** compatible additions only, such as new
keyword arguments with defaults.

```diff
diff -U0 \
  <(scripts/list_apis.sh -d -p --ref v0.7.5) \
  <(scripts/list_apis.sh -d -p)
@@ -156,417 +155,0 @@
-def cake_causal_conv1d_det_train_forward(...)
-def cake_causal_conv1d_det_train_backward(...)
-def cake_causal_conv1d_det(...)
-[Global Functions]
-def cake_causal_conv1d_det_kcp(...)
-def cake_causal_conv1d_det_kcp_multi(...)
-[Global Functions]
-def is_cake_causal_conv1d_nondet_train_supported(...)
-def cake_causal_conv1d_nondet_train_backward_workspace_bytes(...)
-def cake_causal_conv1d_nondet_train_backward_workspace(...)
-def cake_causal_conv1d_nondet_train_forward_workspace_bytes(...)
-def cake_causal_conv1d_nondet_train_forward_workspace(...)
-def cake_causal_conv1d_nondet_train_forward(...)
-def cake_causal_conv1d_nondet_train_backward(...)
-def cake_causal_conv1d_nondet(...)
-[Global Functions]
-def cake_causal_conv1d_nondet_kcp(...)
-def cake_causal_conv1d_nondet_kcp_multi(...)
-[Global Functions]
-def cake_dsa_indexer_det_train_topk(...)
-def cake_dsa_indexer_det_train_topk_workspace_size(...)
-[Global Functions]
-def cake_dsa_indexer_nondet_train_topk(...)
-def cake_dsa_indexer_nondet_train_topk_workspace_size(...)
-[Global Functions]
-def cake_dsa_sparse_attention_det(...)
-def cake_dsa_sparse_attention_det_varlen(...)
-def cake_dsa_sparse_attention_det_nope(...)
-def cake_dsa_sparse_attention_det_nope_varlen(...)
-[Global Functions]
-def cake_dsa_sparse_attention_nondet(...)
-def cake_dsa_sparse_attention_nondet_varlen(...)
-def cake_dsa_sparse_attention_nondet_nope(...)
-def cake_dsa_sparse_attention_nondet_nope_varlen(...)
-[Global Functions]
@@ -623,277 +206,3 @@
-def is_cake_gated_act_mxfp8_det_train_supported(device: torch.device) -> bool:
-
-
-@flashinfer_api(trace=cake_gated_act_mxfp8_det_train_forward_trace_dispatch)
-def cake_gated_act_mxfp8_det_train_forward(
-    gated_input: torch.Tensor,
-    *,
-    rowwise: bool = True,
-    colwise: bool = False,
-) -> CakeGatedActMXFP8DetOutputs:
-
-
-@flashinfer_api(trace=cake_gated_act_mxfp8_det_train_backward_trace_dispatch)
-def cake_gated_act_mxfp8_det_train_backward(
-    gated_input: torch.Tensor,
-    grad_output: torch.Tensor,
-    *,
-    rowwise: bool = True,
-    colwise: bool = False,
-) -> CakeGatedActMXFP8DetOutputs:
-[Global Functions]
-@flashinfer_api
-def cake_gdn_det(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: torch.Tensor,
-    beta: torch.Tensor,
-    scale: Optional[float] = None,
-    initial_state: Optional[torch.Tensor] = None,
-    output_final_state: bool = False,
-    cu_seqlens: Optional[torch.Tensor] = None,
-    cu_seqlens_cpu: Optional[torch.Tensor] = None,
-    use_qk_l2norm_in_kernel: bool = False,
-    *,
-    scan_config: Optional[tuple[int, int]] = None,
-    segment_chunks: Optional[int] = None,
-    finalize: Optional[str] = None,
-    warmup_log2: Optional[float] = None,
-    save_state: bool = True,
-    host_cache: bool = True,
-    dhu_scan: Optional[str] = None,
-    prep: Optional[str] = None,
-    lpt: bool = True,
-    streams: int = 2,
-) -> tuple[torch.Tensor, Optional[torch.Tensor]]:
-
-
-@flashinfer_api
-def is_cake_gdn_det_train_supported(
-    device: torch.device | str | int | None = None,
-) -> bool:
-
-
-
-
-[Global Functions]
-@flashinfer_api
-def cake_gdn_det_train_kcp_partition(
-    cu_seqlens_global_cpu: Any,
-    world_size: int,
-    layout: str = "contiguous",
-    fragments: Optional[Any] = None,
-    *,
-    cut_points: Optional[Any] = None,
-) -> Any:
-
-
-@flashinfer_api
-def cake_gdn_det_train_kcp_build_context(
-    part: Any,
-    group: Any,
-    rank: int,
-    device: Any,
-    conv_kernel_size: int = 4,
-    *,
-    sm_count: Optional[int] = None,
-) -> Any:
-
-
-@flashinfer_api
-def cake_gdn_det_train_kcp_forward(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: torch.Tensor,
-    beta: torch.Tensor,
-    ctx: Any,
-    *,
-    scale: Optional[float] = None,
-    save_for_backward: bool = True,
-    workspace: Optional[Any] = None,
-    options: Optional[Any] = None,
-    use_qk_l2norm_in_kernel: bool = False,
-    **knobs: Any,
-) -> tuple[torch.Tensor, Optional[Any]]:
-
-
-@flashinfer_api
-def cake_gdn_det_train_kcp_backward(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: torch.Tensor,
-    beta: torch.Tensor,
-    ctx: Any,
-    dout: torch.Tensor,
-    *,
-    saved: Optional[Any] = None,
-    scale: Optional[float] = None,
-    workspace: Optional[Any] = None,
-    options: Optional[Any] = None,
-    use_qk_l2norm_in_kernel: bool = False,
-    **knobs: Any,
-) -> tuple[torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor]:
-
-
-@flashinfer_api
-def cake_gdn_det_kcp(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: torch.Tensor,
-    beta: torch.Tensor,
-    ctx: Any,
-    *,
-    scale: Optional[float] = None,
-    save_mode: str = "light",
-    boundary_mode: str = "saved",
-    workspace: Optional[Any] = None,
-    graph: str = "off",
-    options: Optional[Any] = None,
-    recompute_handle: Optional[Any] = None,
-    use_qk_l2norm_in_kernel: bool = False,
-    **knobs: Any,
-) -> torch.Tensor:
-
-@flashinfer_api
-def cake_gdn_det_train_kcp_packed_qkv_views(
-    qkv: torch.Tensor, *, H_qk: int, HV: int
-) -> tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
-
-
-@flashinfer_api
-def cake_gdn_det_train_kcp_workspace_bytes(
-    ctx: Any, *, H_qk: int, HV: int, **kw: Any
-) -> int:
-
-
-@flashinfer_api
-def cake_gdn_det_train_kcp_saved_bytes(
-    ctx: Any, *, H_qk: int, HV: int, **kw: Any
-) -> int:
-
-
-@flashinfer_api
-def cake_gdn_det_train_kcp_comm_bytes(
-    ctx: Any, *, H_qk: int, HV: int, C: int = 10240, **kw: Any
-) -> dict:
-
-
-@flashinfer_api
-def is_cake_gdn_det_train_kcp_supported(
-    device: torch.device | str | int | None = None,
-) -> bool:
-
-
-
-
-
-
-[Global Functions]
-@flashinfer_api
-def cake_gdn_nondet(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: torch.Tensor,
-    beta: torch.Tensor,
-    scale: Optional[float] = None,
-    initial_state: Optional[torch.Tensor] = None,
-    output_final_state: bool = False,
-    cu_seqlens: Optional[torch.Tensor] = None,
-    cu_seqlens_cpu: Optional[torch.Tensor] = None,
-    use_qk_l2norm_in_kernel: bool = False,
-    *,
-    scan_config: Optional[tuple[int, int]] = None,
-    segment_chunks: Optional[int] = None,
-    finalize: Optional[str] = None,
-    warmup_log2: Optional[float] = None,
-    save_state: bool = True,
-    host_cache: bool = True,
-    dhu_scan: Optional[str] = None,
-    prep: Optional[str] = None,
-    lpt: bool = True,
-    streams: int = 2,
-    tail: Optional[str] = None,
-) -> tuple[torch.Tensor, Optional[torch.Tensor]]:
-
-
-@flashinfer_api
-def is_cake_gdn_nondet_train_supported(
-    device: torch.device | str | int | None = None,
-) -> bool:
-
-
-
-
-[Global Functions]
-@flashinfer_api
-def cake_gdn_nondet_train_kcp_partition(
-    cu_seqlens_global_cpu: Any,
-    world_size: int,
-    layout: str = "contiguous",
-    fragments: Optional[Any] = None,
-    *,
-    cut_points: Optional[Any] = None,
-) -> Any:
-
-
-@flashinfer_api
-def cake_gdn_nondet_train_kcp_build_context(
-    part: Any,
-    group: Any,
-    rank: int,
-    device: Any,
-    conv_kernel_size: int = 4,
-    *,
-    sm_count: Optional[int] = None,
-    graph_replay: bool = False,
-) -> Any:
-
-
-@flashinfer_api
-def cake_gdn_nondet_train_kcp_forward(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: torch.Tensor,
-    beta: torch.Tensor,
-    ctx: Any,
-    *,
-    scale: Optional[float] = None,
-    save_for_backward: bool = True,
-    workspace: Optional[Any] = None,
-    options: Optional[Any] = None,
-    **knobs: Any,
-) -> tuple[torch.Tensor, Optional[Any]]:
-
-
-@flashinfer_api
-def cake_gdn_nondet_train_kcp_backward(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: torch.Tensor,
-    beta: torch.Tensor,
-    ctx: Any,
-    dout: torch.Tensor,
-    *,
-    saved: Optional[Any] = None,
-    scale: Optional[float] = None,
-    workspace: Optional[Any] = None,
-    options: Optional[Any] = None,
-    **knobs: Any,
-) -> tuple[torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor]:
-
-
-@flashinfer_api
-def cake_gdn_nondet_kcp(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: torch.Tensor,
-    beta: torch.Tensor,
-    ctx: Any,
-    *,
+def localize_gdn_decode_state(
+    state: torch.Tensor,
+    num_q_heads: int,
@@ -901,7 +210 @@
-    save_mode: Optional[str] = None,
-    boundary_mode: str = "saved",
-    workspace: Optional[Any] = None,
-    graph: str = "off",
-    options: Optional[Any] = None,
-    recompute_handle: Optional[Any] = None,
-    **knobs: Any,
+    rows0: Optional[int] = None,
@@ -910,37 +212,0 @@
-def cake_gdn_nondet_train_kcp_packed_qkv_views(...)
-def cake_gdn_nondet_train_kcp_workspace_bytes(...)
-def cake_gdn_nondet_train_kcp_saved_bytes(...)
-def cake_gdn_nondet_train_kcp_comm_bytes(...)
-def is_cake_gdn_nondet_train_kcp_supported(...)
@@ -964,0 +231,2 @@
+    rand_seed: Optional[torch.Tensor] = None,
+    philox_rounds: int = 10,
@@ -966,1195 +233,0 @@
-[Global Functions]
-def cake_gqa_det(...)
-def cake_gqa_det_train_forward(...)
-def cake_gqa_det_train_backward(...)
-def cake_gqa_det_train_workspace(...)
-def cake_gqa_det_train_workspace_bytes(...)
-[Global Functions]
-def cake_gqa_nondet(...)
-def cake_gqa_nondet_train_forward(...)
-def cake_gqa_nondet_train_backward(...)
-def cake_gqa_nondet_train_workspace(...)
-def cake_gqa_nondet_train_workspace_bytes(...)
-[Global Functions]
-def cake_kda_det_train_forward(...)
-def cake_kda_det_train_backward(...)
-def cake_kda_det(...)
-[Global Functions]
-def cake_kda_det_train_kcp_partition(...)
-def cake_kda_det_train_kcp_build_context(...)
-def cake_kda_det_train_kcp_forward(...)
-def cake_kda_det_train_kcp_backward(...)
-def cake_kda_det_kcp(...)
-def cake_kda_det_train_kcp_workspace_bytes(...)
-def cake_kda_det_train_kcp_reduce_gate_param_grads(...)
-def cake_kda_det_train_kcp_saved_bytes(...)
-def cake_kda_det_train_kcp_comm_bytes(...)
-[Global Functions]
-def cake_kda_nondet_train_forward(...)
-def cake_kda_nondet_train_backward(...)
-def cake_kda_nondet(...)
-[Global Functions]
-def cake_kda_nondet_train_kcp_partition(...)
-def cake_kda_nondet_train_kcp_build_context(...)
-def cake_kda_nondet_train_kcp_forward(...)
-def cake_kda_nondet_train_kcp_backward(...)
-def cake_kda_nondet_kcp(...)
-def cake_kda_nondet_train_kcp_workspace_bytes(...)
-def cake_kda_nondet_train_kcp_reduce_gate_param_grads(...)
-def cake_kda_nondet_train_kcp_saved_bytes(...)
-def cake_kda_nondet_train_kcp_handoff_bytes(...)
-def cake_kda_nondet_train_kcp_handoff_stats(...)
-def cake_kda_nondet_train_kcp_comm_bytes(...)
-[Global Functions]
-def cake_lm_head_det_train_loss(...)
-def cake_lm_head_det_train_logprob(...)
-def cake_lm_head_det_train_preload(...)
-def cake_lm_head_det_train_support_logprob(...)
-def cake_lm_head_det_train_support_kl(...)
-[Global Functions]
-def cake_lm_head_nondet_train_loss(...)
-def cake_lm_head_nondet_train_logprob(...)
-def cake_lm_head_nondet_train_preload(...)
-def cake_lm_head_nondet_train_support_logprob(...)
-def cake_lm_head_nondet_train_support_kl(...)
-[Global Functions]
-def cake_mhc_det_train_forward_workspace_bytes(...)
-def cake_mhc_det_train_backward_workspace_bytes(...)
-def cake_mhc_det_train_forward_prepare(...)
-def cake_mhc_det_train_forward_stats(...)
-def cake_mhc_det_train_forward_finish(...)
-def cake_mhc_det_train_backward_prepare(...)
-def cake_mhc_det_train_backward_finish(...)
-def cake_mhc_det_train_prepare(...)
-def cake_mhc_det_train_finish(...)
-[Global Functions]
-def cake_mhc_head_det_train_forward(...)
-def cake_mhc_head_det_train_backward(...)
-def cake_mhc_head_det(...)
-[Global Functions]
-def cake_mhc_head_nondet_train_forward(...)
-def cake_mhc_head_nondet_train_backward(...)
-def cake_mhc_head_nondet(...)
-[Global Functions]
-def is_cake_mhc_nondet_train_supported(...)
-def cake_mhc_nondet_train_forward_workspace_bytes(...)
-def cake_mhc_nondet_train_backward_workspace_bytes(...)
-def cake_mhc_nondet_train_forward_workspace(...)
-def cake_mhc_nondet_train_backward_workspace(...)
-def cake_mhc_nondet_train_forward_prepare(...)
-def cake_mhc_nondet_train_forward_stats(...)
-def cake_mhc_nondet_train_forward_finish(...)
-def cake_mhc_nondet_train_backward_prepare(...)
-def cake_mhc_nondet_train_backward_finish(...)
-def cake_mhc_nondet_train_prepare(...)
-def cake_mhc_nondet_train_finish(...)
@@ -2220,359 +292,0 @@
-def cake_moe_grouped_gemm_det_train_forward(...)
-def cake_moe_grouped_gemm_det_train_dgrad(...)
-def cake_moe_grouped_gemm_det_train_wgrad(...)
-def cake_moe_grouped_gemm_det_train_prepare_forward(...)
-def cake_moe_grouped_gemm_det_train_prepare_dgrad(...)
-def cake_moe_grouped_gemm_det_train_prepare_wgrad(...)
-def cake_moe_grouped_gemm_det(...)
-def is_cake_moe_grouped_gemm_det_train_supported(...)
-[Global Functions]
-def cake_moe_grouped_gemm_nondet_train_forward(...)
-def cake_moe_grouped_gemm_nondet_train_dgrad(...)
-def cake_moe_grouped_gemm_nondet_train_wgrad(...)
-def cake_moe_grouped_gemm_nondet_train_prepare_forward(...)
-def cake_moe_grouped_gemm_nondet_train_prepare_dgrad(...)
-def cake_moe_grouped_gemm_nondet_train_prepare_wgrad(...)
-def cake_moe_grouped_gemm_nondet(...)
-def is_cake_moe_grouped_gemm_nondet_train_supported(...)
-[Global Functions]
-def cake_rmsnorm_det_train_forward(...)
-def cake_rmsnorm_det_train_backward(...)
-def cake_rmsnorm_det(...)
-[Global Functions]
-def cake_rmsnorm_nondet_train_forward(...)
-def cake_rmsnorm_nondet_train_backward(...)
-def cake_rmsnorm_nondet(...)
-[Global Functions]
-def is_cake_rmsnorm_silu_gate_det_train_supported(...)
-def cake_rmsnorm_silu_gate_det_train_forward(...)
-def cake_rmsnorm_silu_gate_det_train_backward_workspace_bytes(...)
-def cake_rmsnorm_silu_gate_det_train_backward_workspace(...)
-def cake_rmsnorm_silu_gate_det_train_reset_workspace(...)
-def cake_rmsnorm_silu_gate_det_train_backward(...)
-def cake_rmsnorm_silu_gate_det(...)
-[Global Functions]
-def is_cake_rmsnorm_silu_gate_nondet_train_supported(...)
-def cake_rmsnorm_silu_gate_nondet_train_forward(...)
-def cake_rmsnorm_silu_gate_nondet_train_backward_workspace_bytes(...)
-def cake_rmsnorm_silu_gate_nondet_train_backward_workspace(...)
-def cake_rmsnorm_silu_gate_nondet_train_reset_workspace(...)
-def cake_rmsnorm_silu_gate_nondet_train_backward(...)
-def cake_rmsnorm_silu_gate_nondet(...)
-[Global Functions]
@@ -3352 +1066 @@
-@flashinfer_api(trace=decode_cp_a2a_lse_reduce_trace)
+@flashinfer_api(trace=decode_cp_a2a_lse_reduce_trace_dispatch)
@@ -3359,0 +1074,2 @@
+    *,
+    mask: Optional[torch.Tensor] = None,
@@ -4096 +1812 @@
-    backend: str = "cute",
+    backend: str = "auto",
@@ -5726,2 +3442,2 @@
-    backend: Literal["cake"] = "cake",
-    fallback: bool = True,
+    backend: Literal["cake", "blackwell"] = "cake",
+    fallback: Optional[bool] = None,
@@ -6101,0 +3818,16 @@
+    localized_weights: Optional[List[Dict[str, torch.Tensor]]],
+    localized_streams: Optional[List[Any]],
+    localized_sm_count: Optional[int],
+    device: torch.device,
+) -> Tuple[List[torch.Tensor], List[int], int]:
+
+
+@flashinfer_api
+def split_fp4_moe_weights_by_locality_domain(
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+    gemm2_weights: torch.Tensor,
+    gemm2_weights_scale: torch.Tensor,
+    num_domains: int = 2,
+) -> List[Dict[str, torch.Tensor]]:
+
@@ -6142,0 +3875,4 @@
+    localized_weights: Optional[List[Dict[str, torch.Tensor]]] = None,
+    localized_streams: Optional[List[Any]] = None,
+    localized_sm_count: Optional[int] = None,
+    fc2_input_out: Optional[Tuple[torch.Tensor, torch.Tensor, torch.Tensor]] = None,
@@ -6186,0 +3923,4 @@
+    localized_weights: Optional[List[Dict[str, torch.Tensor]]] = None,
+    localized_streams: Optional[List[Any]] = None,
+    localized_sm_count: Optional[int] = None,
+    fc2_input_out: Optional[Tuple[torch.Tensor, torch.Tensor, torch.Tensor]] = None,
@@ -6465,0 +4206 @@
+    localized_options: Optional[dict] = None,
@@ -7042,0 +4784,2 @@
+
+
@@ -7061,0 +4805,20 @@
+    key: tuple, state: torch.Tensor, homed
+) -> Optional[tuple]:
+
+
+
+
+    key: tuple, homed, launch: tuple, error: Exception
+) -> None:
+
+
+    key: tuple, whole: tuple, state: torch.Tensor, homed
+) -> tuple:
+
+
+
+
+
+
+
+
@@ -7234,0 +4998,55 @@
+    *,
+    capability: tuple[int, int],
+    num_seqs: int,
+    num_sab_heads: int,
+    seqlen_bound: int,
+    io_dtype: torch.dtype,
+) -> bool:
+
+
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    state_pool: torch.Tensor,
+    page_size: int,
+) -> Optional[str]:
+
+
+
+
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    state_pool: torch.Tensor,
+    output: Optional[torch.Tensor],
+    *,
+    num_seqs: int,
+    page_size: int,
+    max_seqlen: Optional[int],
+    aligned_prefixes: bool,
+) -> bool:
+
+
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    g: Optional[torch.Tensor],
+    beta: Optional[torch.Tensor],
+    scale: Optional[float],
+    *,
+    cu_seqlens: torch.Tensor,
+    state_pool: torch.Tensor,
+    page_indices: torch.Tensor,
+    page_size: int,
+    slots: GDNPagedPrefillSlots,
+    use_qk_l2norm_in_kernel: bool,
+    output: Optional[torch.Tensor],
+    gate_domain: str,
+    use_gate_in_kernel: bool,
+    A_log: Optional[torch.Tensor],
+    dt_bias: Optional[torch.Tensor],
+    beta_is_logit: bool,
+    max_seqlen: Optional[int],
+) -> torch.Tensor:
+
+
@@ -7257,0 +5076,3 @@
+    backend: Literal["flashinfer", "cake_gdn", "auto"] = "flashinfer",
+    max_seqlen: Optional[int] = None,
+    aligned_prefixes: bool = False,
@@ -7313,0 +5135,4 @@
+    use_affine_split: bool = False,
+    _affine_split_count: Optional[int] = None,
+    batch_invariant: bool = False,
+    train_states: Optional[torch.Tensor] = None,
@@ -7809,0 +5635 @@
+    bias: Optional[torch.Tensor] = None,
@@ -7818,0 +5645 @@
+    bias: Optional[torch.Tensor] = None,
@@ -7827,0 +5655 @@
+    bias: Optional[torch.Tensor] = None,
@@ -7836,0 +5665 @@
+    bias: Optional[torch.Tensor] = None,
@@ -7845,0 +5675 @@
+    bias: Optional[torch.Tensor] = None,
@@ -7857,0 +5688 @@
+    bias: Optional[torch.Tensor] = None,
@@ -7859 +5690 @@
-@flashinfer_api(trace=bmm_fp8_trace)
+@flashinfer_api(trace=bmm_fp8_trace_dispatch)
@@ -7869,0 +5701 @@
+    bias: Optional[torch.Tensor] = None,
@@ -8141,0 +5974,2 @@
+
+
@@ -8267,0 +6102,14 @@
+@flashinfer_api
+def mm_mxfp8_mxfp4(
+    a: torch.Tensor,
+    b: torch.Tensor,
+    a_descale: torch.Tensor,
+    b_descale: torch.Tensor,
+    alpha: Optional[torch.Tensor] = None,
+    out_dtype: torch.dtype = torch.bfloat16,
+    out: Optional[torch.Tensor] = None,
+    *,
+    batch_invariant: bool = False,
+    enable_pdl: Optional[bool] = None,
+) -> torch.Tensor:
+[Global Functions]
@@ -8344,0 +6193,9 @@
+    activation_type: Optional[Union[ActivationType, int]] = None,
+    swiglu_alpha: float = DEFAULT_SWIGLU_ALPHA,
+    swiglu_beta: float = DEFAULT_SWIGLU_BETA,
+    swiglu_limit: float = DEFAULT_SWIGLU_LIMIT,
+    alpha_up: Optional[torch.Tensor] = None,
+    a_per_token_scale: Optional[torch.Tensor] = None,
+    out_scale: Optional[torch.Tensor] = None,
+    out_global_scale: Optional[torch.Tensor] = None,
+    nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
@@ -8585,0 +6443 @@
+    batch_invariant: bool = False,
@@ -8928,0 +6787,6 @@
+    state_dtype: Optional[torch.dtype] = None,
+    final_states: Optional[torch.Tensor] = None,
+    initial_state_slots: Optional[torch.Tensor] = None,
+    final_state_slots: Optional[torch.Tensor] = None,
+    initial_state_flags: Optional[torch.Tensor] = None,
+    null_slot_id: int = -1,
@@ -9244,0 +7109,46 @@
+
+
+    arch: str,
+    num_sms: int,
+    dtype: torch.dtype,
+    page_size: int,
+    q_len: int,
+    has_sinks: bool,
+    max_seq_len: int,
+) -> Tuple[Tuple[str, int, int], ...]:
+
+
+    arch: str,
+    num_sms: int,
+    dtype: torch.dtype,
+    page_size: int,
+    domain: str,
+    q_len: int,
+    has_sinks: bool,
+    max_seq_len: int,
+    batch_size: int,
+) -> bool:
+
+
+
+
+    device_index: int,
+    dtype: torch.dtype,
+    page_size: int,
+    q_len: int,
+    has_sinks: bool,
+    max_seq_len: int,
+) -> Tuple[Tuple[int, int], ...]:
+
+
+    device_facts: Callable[[int], Tuple[str, int]],
+    device_index: int,
+    dtype: torch.dtype,
+    page_size: int,
+    q_len: int,
+    seq_bucket: int,
+) -> Tuple[Tuple[int, int], ...]:
+
+
+
+
@@ -9278,0 +7189,10 @@
+    workspace_sizer,
+    resolved_impl: str,
+    workspace_bytes: int,
+    q_len: int,
+    num_heads: int,
+    kv_lora_rank: int,
+    max_active_blocks: int,
+    max_seq_len: int,
+    candidate_max: int,
+) -> int:
@@ -9304 +7224,10 @@
-    backend: str,
+    kv_cache: torch.Tensor,
+    block_tables: torch.Tensor,
+    seq_lens: torch.Tensor,
+    out: torch.Tensor,
+    qk_nope_head_dim: int,
+    kv_lora_rank: int,
+    qk_rope_head_dim: int,
+    sparse_mla_top_k: int,
+    bmm1_scale: Union[float, torch.Tensor],
+    bmm2_scale: Union[float, torch.Tensor],
@@ -9306,3 +7235,6 @@
-    cum_seq_lens_q: Optional[torch.Tensor],
-    max_q_len: Optional[int],
-    return_lse: bool,
+    skip_softmax_threshold_scale_factor: Optional[float],
+    uses_shared_paged_kv_idx: bool,
+    lse_requested: bool,
+    use_fp16_softmax: Optional[bool],
+    multi_ctas_kv_counter_buffer: Optional[torch.Tensor],
+    sparse_mla_top_k_lens: Optional[torch.Tensor],
@@ -9310,4 +7242 @@
-    cp_world: int,
-    cp_rank: int,
-    causal_seqlens_kv_global: Optional[torch.Tensor],
-) -> str:
+) -> Optional[str]:
@@ -9316,2 +7245 @@
-    query: torch.Tensor,
-    out_dtype: torch.dtype,
+    *,
@@ -9320 +7247,0 @@
@@ -9321,0 +7249 @@
+    sparse_mla_top_k_lens: Optional[torch.Tensor],
@@ -9322,0 +7251,4 @@
+    lse_requested: bool,
+    use_fp16_softmax: Optional[bool],
+    enable_dcp: bool,
+    multi_ctas_kv_counter_buffer: Optional[torch.Tensor],
@@ -9324,2 +7256,4 @@
-    qk_rope_head_dim: int,
-    kv_lora_rank: int,
+) -> Optional[str]:
+    capability: Tuple[int, int],
+    dtype: torch.dtype,
+    kv_dtype: torch.dtype,
@@ -9327,7 +7261,9 @@
-    is_var_seq: bool,
-    use_fp16_softmax: Optional[bool] = None,
-    cute_dsl_impl: str = "auto",
-    cum_seq_lens_q: Optional[torch.Tensor] = None,
-    max_q_len: Optional[int] = None,
-    enable_dcp: bool = False,
-    cp_world: int = 1,
+    bmm1_scale: float,
+    bmm2_scale: float,
+    seq_lens_dtype: torch.dtype,
+    block_tables_dtype: torch.dtype,
+    qk_nope_head_dim: int,
+    kv_lora_rank: int,
+    qk_rope_head_dim: int,
+    num_heads: int,
+    has_sinks: bool,
@@ -9335,10 +7270,0 @@
@@ -11039,0 +8966,41 @@
+    causal=True,
+):
+
+
+    device,
+    layout,
+    q_dtype,
+    kv_dtype,
+    o_dtype,
+    head_dim_qk,
+    head_dim_vo,
+    batch,
+    hq,
+    hk,
+    max_q,
+    max_kv,
+    page_size,
+    total_q,
+    qo_indptr_host,
+    kv_lens,
+    seq_lens_q=None,
+):
+
+
+    device,
+    layout,
+    q_dtype,
+    kv_dtype,
+    o_dtype,
+    head_dim_qk,
+    head_dim_vo,
+    batch,
+    hq,
+    hk,
+    max_q,
+    max_kv,
+    page_size,
+    total_q,
+    qo_indptr_host,
+    kv_lens,
+    seq_lens_q=None,
@@ -12188,0 +10156 @@
+    out: Optional[torch.Tensor] = None,
@@ -12200,0 +10169,6 @@
+    out: Optional[torch.Tensor] = None,
+    lse_out: Optional[torch.Tensor] = None,
+    top_k: Optional[Union[int, torch.Tensor]] = None,
+    top_p: Optional[Union[float, torch.Tensor]] = None,
+    min_p: Optional[Union[float, torch.Tensor]] = None,
+    filter_apply_order: str = "top_k_first",
@@ -12210,0 +10185,2 @@
+    out_dtype: Optional[torch.dtype] = None,
+    out: Optional[torch.Tensor] = None,
@@ -12223 +10199,7 @@
-) -> torch.Tensor:
+    *,
+    batch_invariant: bool = False,
+    temperature: Optional[Union[torch.Tensor, float]] = None,
+    return_logprob: bool = False,
+    out: Optional[torch.Tensor] = None,
+    logprob_out: Optional[torch.Tensor] = None,
+) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
@@ -12235,0 +10218,3 @@
+    *,
+    batch_invariant: bool = False,
+    out: Optional[torch.Tensor] = None,
@@ -12249,0 +10235,3 @@
+    *,
+    batch_invariant: bool = False,
+    out: Optional[torch.Tensor] = None,
@@ -12263,0 +10252,3 @@
+    *,
+    batch_invariant: bool = False,
+    out: Optional[torch.Tensor] = None,
@@ -12277,0 +10269,3 @@
+    *,
+    batch_invariant: bool = False,
+    out: Optional[torch.Tensor] = None,
@@ -12316 +10310,9 @@
-) -> torch.Tensor:
+    *,
+    batch_invariant: bool = False,
+    temperature: Optional[Union[torch.Tensor, float]] = None,
+    return_logprob: bool = False,
+    return_kept_logprob: bool = False,
+    out: Optional[torch.Tensor] = None,
+    logprob_out: Optional[torch.Tensor] = None,
+    kept_logprob_out: Optional[torch.Tensor] = None,
+) -> Union[torch.Tensor, Tuple[torch.Tensor, ...]]:
@@ -12332,0 +10335,3 @@
+    *,
+    batch_invariant: bool = False,
+    out: Optional[torch.Tensor] = None,
@@ -12493,0 +10499,65 @@
+
+
+
+
+    positions, block_table, out, block_tables, seq_lens, rows, dim, device
+):
+
+
+
+
+
+
+
+
+
+
+@flashinfer_api(trace=gather_nvfp4_kv_cache_by_position_trace)
+def gather_nvfp4_kv_cache_by_position(
+    paged_kv_cache: tuple[torch.Tensor, torch.Tensor],
+    kv_cache_sf: tuple[torch.Tensor, torch.Tensor],
+    positions: torch.Tensor,
+    requests: torch.Tensor,
+    block_table: torch.Tensor,
+    *,
+    out: torch.Tensor,
+    block_tables: torch.Tensor,
+    seq_lens: torch.Tensor,
+    lengths: torch.Tensor | None = None,
+    requests_per_row: int = 1,
+    v_sf_swizzled: bool = True,
+    tokens_per_program: int = 32,
+    num_warps: int = 4,
+) -> None:
+
+
+
+
+
+
+@flashinfer_api(trace=compact_nvfp4_kv_cache_trace)
+def compact_nvfp4_kv_cache(
+    paged_kv_cache: tuple[torch.Tensor, torch.Tensor],
+    kv_cache_sf: tuple[torch.Tensor, torch.Tensor],
+    positions: torch.Tensor,
+    row_groups: torch.Tensor,
+    group_requests: torch.Tensor,
+    block_table: torch.Tensor,
+    group_offsets: torch.Tensor,
+    *,
+    out: torch.Tensor,
+    block_tables: torch.Tensor,
+    seq_lens: torch.Tensor,
+    scratch: torch.Tensor,
+    bitmap: torch.Tensor,
+    max_keys: int,
+    max_capacity: int,
+    zero_row: int,
+    group_base: int = 0,
+    group_dense: torch.Tensor | None = None,
+    lengths: torch.Tensor | None = None,
+    requests_per_row: int = 1,
+    v_sf_swizzled: bool = True,
+    tokens_per_program: int = 32,
+    num_warps: int = 4,
+) -> None:
@@ -12595,0 +10666,36 @@
+    num_rows: int,
+    num_kv_heads: int,
+    num_tiles: int,
+    kv_format: int,
+    resident: Tuple[int, int],
+) -> int:
+
+
+
+
+    tensor: torch.Tensor, name: str, num_bytes: int, stride: Tuple[int, ...]
+) -> None:
+
+
+    q: torch.Tensor,
+    k_cache: torch.Tensor,
+    v_cache: torch.Tensor,
+    logical_indices: torch.Tensor,
+    block_table: torch.Tensor,
+    token_to_req: torch.Tensor,
+    use_prefill_config: bool,
+    out: Optional[torch.Tensor] = None,
+    k_scale: Optional[float] = None,
+    v_scale: Optional[float] = None,
+    *,
+    output_gate: torch.Tensor,
+    k_sf: Optional[torch.Tensor] = None,
+    v_sf: Optional[torch.Tensor] = None,
+) -> torch.Tensor:
+
+
+
+
+[Global Functions]
+@flashinfer_api(trace=qsa_sparse_paged_attention_trace)
+def qsa_sparse_paged_attention(
```


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
  * Updated the app version from 0.7.5 to 0.7.6.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: jimmzhou <jimmzhou@nvidia.com>

### [05cad9a](https://github.com/flashinfer-ai/flashinfer/commit/05cad9ac4ee4f278efe4d284a29f60cd595bb422)

- **作者**: Adrian
- **时间**: 2026-11-25T01:04:17Z
- **提交信息**: fix(ci): preserve newer NCCL wheels in EP setup (#10006)

<!-- .github/pull_request_template.md -->

## 📌 Description

The cu134 Python 3.11 image used by #9334 includes PyTorch requiring
NCCL 2.32.3. EP setup defaults to NCCL 2.30.7 and reasserts that pin
after installing FlashInfer, causing PyTorch import to fail with
`undefined symbol: ncclReduceConfig`.

Default to the newer of the installed NCCL wheel and the EP minimum,
2.30.7. Preserve explicit `FI_NCCL_VERSION` overrides and reuse the
selected version throughout setup.

## 🔍 Related Issues

Related: #9334, #9990.

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

Validation:
- An isolated metadata harness reproduced the incorrect 2.32.3-to-2.30.7
selection before the change.
- Six selection cases pass: newer installed version, exact floor, two
older versions, missing wheel, and explicit override.
- Changed-file pre-commit hooks, `bash -n`, and `git diff --check`
passed.

No new tests were added. Full EP setup and GPU validation remain to be
run; rerun the affected cu134 multi-GPU EP lane for runtime validation.

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/infra/test_sharding/test_shell_entrypoint.py`

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

The change is limited to the EP setup script; it preserves the minimum
required by EP without downgrading newer image-provided NCCL wheels. AI
assistance: prepared and reviewed with Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Build setup now uses the installed CUDA-matched NCCL version when
available, with a minimum version of 2.30.7. This helps keep the
selected NCCL version aligned with the installed runtime.
* Updated build guidance to reflect the version selection and clarify
how package constraints are applied.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [3e2fae8](https://github.com/flashinfer-ai/flashinfer/commit/3e2fae8e6117ab49e4ac12cf2fea6d55e1578476)

- **作者**: Adrian
- **时间**: 2026-11-25T01:04:05Z
- **提交信息**: fix(ci): constrain cuda-core to match image bindings (#10005)

<!-- .github/pull_request_template.md -->

## 📌 Description

The Python 3.11 CI images used by #9334 resolve `cuda-core==1.3.1`
alongside bindings that cannot satisfy its runtime floor. NVSHMEM test
collection fails with bindings 12.9.7 on cu129 and 13.0.3 on cu130.

Constrain the image dependency resolver to `cuda-core<1.3`, preserving
the existing CUDA Python selections. Version 1.3.0 has the same
incompatible bindings floors as 1.3.1, so excluding only 1.3.1 is
insufficient.

## 🔍 Related Issues

Related: #9334, #9990.

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

Validation:
- Reproduced the `cuda.core 1.3.1` import failure with bindings 13.0.3
in an isolated Python 3.11 environment.
- With the constraint, `cuda-core==1.2.2` imports `MemoryResource` and
`Buffer` with bindings 12.9.7, 13.0.3, and 13.4.1.
- Existing image tests: `PYTHONPATH=. python -m pytest
--confcutdir=tests/cpu tests/cpu/infra/test_cuda_tile_ci.py -q` — 29
passed.
- Changed-file pre-commit hooks, `bash -n`, and `git diff --check`
passed.

No new tests were added. Full Docker image builds and GPU tests remain
to be run.

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/infra/test_cuda_tile_ci.py`

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

Rebuild CI images after merging, then update their pins and rerun
NVSHMEM collection. AI assistance: prepared and reviewed with Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Added a CUDA core package to the application’s installation
dependencies.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f029468](https://github.com/flashinfer-ai/flashinfer/commit/f0294689bf607055eb3aa0179cb9c0537a4cade4)

- **作者**: FlashInfer Bot
- **时间**: 2026-11-25T01:01:36Z
- **提交信息**: Update Docker CI tags to 20261124-98c130a (#9334)

This PR updates the Docker CI image tags to the latest version:
`20261124-98c130a`

The image list is generated from `ci/cuda-versions.json`.

Auto-generated by [release-ci-docker
workflow](https://github.com/flashinfer-ai/flashinfer/actions/runs/45473788855)

Co-authored-by: righthandabacus <12358258+righthandabacus@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4861
- **最后更新**: 2026-11-26T03:10:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34978
- **最后更新**: 2026-11-26T03:28:03Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Lucain, DoronGenzelHass

## AI分析总结

# `huggingface/diffusers` 昨日提交分析

## 1. 主要更新类型
- **功能新增为主**：LTX-2.5 扩散解码器新增"关键帧感知解码"能力；
- **附带小幅改进/重构**：关键帧输入改为可选参数、移除模块化集成、裁剪测试；
- **元数据/生态优化**：模型卡片推送时自动打上 `hf_jobs` 标签。

## 2. 关键变更点及与项目方向的关系
- 在 `LTX2VideoDiffusionDecoderModel.decode`、`LTX2VideoDiffusionDecodePipeline` 及相关解码步骤中引入可选的 `keyframe_latents` 与 `keyframe_frame_indices`，使视频解码能以关键帧为锚点组织信息。
- 每个视频位置会注意力于**最近的两个关键帧平面**，这些平面携带通过 `decoder_keyframe_type_embedding` 启用的可学习 `decoder.type_emb` 标签；转换器在原 VAE 含该标签时会自动开启该标志，保证权重迁移的兼容性。
- 与项目"将前沿视频扩散模型（LTX 系列）模块化、易用化接入 diffusers"的整体方向高度一致：既支持新架构的特殊解码机制，又通过**可选参数**设计保持 API 向后兼容，避免强迫所有用户承担额外复杂度。
- `hf_jobs` 标签提交则服务于 HuggingFace 生态协同：让通过 HF Jobs 推送的模型卡可被自动识别，强化了 diffusers 与 Hub 工作流的联动。

## 3. 对项目的影响与潜在意义
- **质量层面**：关键帧约束有助于改善长视频解码的时间一致性与结构稳定性，缓解扩散视频模型常见的漂移问题，直接提升 LTX-2.5 输出质量。
- **性能/灵活性层面**：不传关键帧时行为与原实现一致，用户可平滑升级；关键帧策略（插槽规则、首个关键帧之前的帧处理）经过与参考实现对齐，降低了与官方实现结果不一致的风险。
- **可维护性层面**：开发者先做模块化集成后又回退，说明社区在"深度插件化"与"接口简洁性"之间做了权衡，最终选择了更轻量的可选前向参数方案，减少长期维护负担。
- **生态层面**：`hf_jobs` 标签提升了模型卡的可发现性和溯源能力，对整个 HuggingFace 平台的作业追踪有边际价值。

## 4. 值得关注的技术点
- **关键帧作为注意力锚点**：视频 token 仅关注最近两个关键帧平面，是稀疏注意力/条件化解码的典型设计，兼顾成本与效果。
- **类型嵌入（type embedding）的条件传递**：通过转换器自动检测并启用 `decoder_keyframe_type_embedding`，体现了权重转换工具在跨版本兼容中的关键角色。
- **测试策略**："trim the keyframe tests" 表明在保持覆盖的前提下精简用例，提示后续关注关键帧边界情况（首帧前、多关键帧间隔）是否仍有回归风险。
- **协作模式**：第二条提交由 Claude Opus 5.5 协作完成，反映 AI 辅助贡献在该仓库已常态化。

## 5. 基于项目背景的整体发展影响
Diffusers 作为开源扩散模型推理/训练的核心库，其价值在于快速、统一地承载最新研究成果。这两条提交分别体现了该路线的两个侧面：**前者把 LTX-2.5 这类前沿视频扩散模型的关键技术细节（关键帧解码）以兼容、渐进的方式落地到主干代码中，确保库不落后于研究进展**；**后者则强化与 HuggingFace 平台基础设施的整合，提升模型发布与追踪的工程化水平**。二者共同推动项目在"研究前沿的快速跟进"与"生产可用的工程稳定性"之间保持平衡，是 diffusers 持续扩大在视频生成领域影响力的典型例证。随着更多支持关键帧/结构化条件的视频模型接入，这类条件化解码接口很可能成为后续统一抽象的雏形。

## 详细提交记录

### [16eb5cc](https://github.com/huggingface/diffusers/commit/16eb5cc4fd8262fd33b3c9119a12977c25cc4985)

- **作者**: DoronGenzelHass
- **时间**: 2026-11-25T22:43:58Z
- **提交信息**: [LTX-2.5] Keyframe-aware decoding for the diffusion decoder (#15244)

* [LTX-2.5] Keyframe-aware decoding for the diffusion decoder

Add optional `keyframe_latents` / `keyframe_frame_indices` to
`LTX2VideoDiffusionDecoderModel.decode`, `LTX2VideoDiffusionDecodePipeline`
and the modular `LTX2DiffusionVaeDecoderStep`. Each video position also
attends to its two nearest keyframe planes, which carry the learned
`decoder.type_emb` tag enabled by `decoder_keyframe_type_embedding`. The
converter sets that flag when the original VAE has the tag.

* [LTX-2.5] Match the reference slot rule for frames before the first keyframe plane

* [LTX-2.5] Take keyframe inputs as optional forward args and drop the modular integration

* [LTX-2.5] Trim the keyframe tests

---------

Co-authored-by: YiYi Xu <yixu310@gmail.com>

### [3d33683](https://github.com/huggingface/diffusers/commit/3d336834a7855493cb665b20db99bdcf0be8c7e8)

- **作者**: Lucain
- **时间**: 2026-11-25T15:49:39Z
- **提交信息**: Add `hf_jobs` tag to model cards when pushing from HF Jobs (#15404)

Add hf_jobs tag to model cards when pushing from HF Jobs

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
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


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13442
- **最后更新**: 2026-11-25T14:31:09Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Jinyan Ye, Hong Zhang

## AI分析总结

## DiffSynth-Studio 昨日提交分析（3条提交）

### 1. 主要更新类型
- **功能新增**：支持MiniMax-H3-pi-H3模型、mesh group与CFG并行
- **性能优化**：VAE decode加速、批量tile编码

---

### 2. 关键变更点及与项目方向的关系

**性能优化（4f67cdf）**
- 加速H3-Image模型的VAE解码过程，增加tile批量编码能力
- DiffSynth-Studio作为扩散模型工作台，推理性能直接决定用户体验，VAE编码/解码是生成流程的瓶颈之一

**模型支持（f82f5e1）**
- 新增MiniMax-H3-pi-H3模型支持，包含下载、加载、LoRA修复
- 体现项目持续扩展模型生态的定位，涵盖视频、图像等多种扩散模型架构

**并行加速（e46ba5b）**
- 支持CFG（Classifier-Free Guidance）并行和mesh group机制，配套文档更新
- CFG是扩散模型采样中计算开销较大的部分，并行化可显著提升推理速度

---

### 3. 对项目的影响和潜在意义

- **推理效率提升**：VAE加速和CFG并行双管齐下，缩短生成时间，适合大规模批量生成场景
- **模型覆盖面扩大**：MiniMax-H3系列的支持表明项目紧跟业界新模型发布节奏
- **生产可用性增强**：LoRA加载修复和下载问题解决，降低了新用户上手门槛
- **社区协作活跃**：三条PR均通过GitHub协作流程合并，反映社区贡献活跃

---

### 4. 值得关注的技术点

- **Tile批量编码策略**：在显存有限的条件下通过分块+批量处理平衡速度与内存
- **CFG并行实现**：需要同时维护两次前向传播的并行调度，对多卡场景尤其重要
- **mesh group机制**：可能是针对大规模生成任务的分组调度抽象，值得深入研究其设计思路

---

### 5. 结合项目背景对发展的影响

DiffSynth-Studio定位为统一的扩散模型推理与训练平台，这批提交体现了三个发展方向：**性能、广度和易用性**。性能优化（VAE+CFG并行）使平台在生产环境中更具竞争力；新模型支持延续了"一站式多模型工作台"的核心价值；文档同步和bug修复则改善了开发者体验。三者共同推动项目从"研究工具"向"生产级推理框架"演进，符合其作为ModelScope生态核心组件的战略定位。

## 详细提交记录

### [4f67cdf](https://github.com/modelscope/DiffSynth-Studio/commit/4f67cdf053341ee19a1995b99f3edce76ec11d1c)

- **作者**: Hong Zhang
- **时间**: 2026-11-25T10:19:56Z
- **提交信息**: accelerate h3-image vae decode (#1859)

* accelerate h3-image vae decode

* tile batch encode

### [f82f5e1](https://github.com/modelscope/DiffSynth-Studio/commit/f82f5e19fdc2dc6660aeb7b3d44b74c7ba8f5cd9)

- **作者**: Jinyan Ye
- **时间**: 2026-11-25T07:31:43Z
- **提交信息**: Support MiniMax-H3-pi-H3 (#1856)

* Add MiniMax-H3-pi-H3

* fix

* fix download

* fix load_lora

### [e46ba5b](https://github.com/modelscope/DiffSynth-Studio/commit/e46ba5b433b092a7cd73e002cb1b5dfa5db08c70)

- **作者**: Hong Zhang
- **时间**: 2026-11-25T05:50:00Z
- **提交信息**: Support mesh group and cfg parallel (#1858)

* cfg parallel

* update docs with cfg parallel

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 39068
- **最后更新**: 2026-11-26T04:02:24Z

## 提交统计

- **昨日提交总数**: 55
- **提交者数量**: 35
- **主要提交者**: ishandhanani, YAMY, Haojie Song

## AI分析总结

# SGLang 昨日提交分析（共55条）

## 1. 主要更新类型分布
- **Bug修复**：约24条（44%），占比最高
- **性能优化**：约9条
- **功能新增**：约8条
- **文档更新**：约9条
- **CI/测试**：约9条
- **重构/杂项**：其余为代码清理与工程化改进

## 2. 关键变更点与项目方向的关系

**推理核心正确性修复**：调度器在上下文边界处的 `max_new_tokens` 裁剪、`req_to_token` 表格按行宽分配内存、disaggregation 状态锁原子性等修复，直接关系到 SGLang 作为高吞吐 LLM 推理引擎的可靠性——这类边界条件 bug 在长上下文和 PD 分离场景下会触发崩溃或越界。

**多硬件生态扩展**：大量 AMD MI355X（inkling2 内核：attention、MoE routing、norm/sconv/MTP）、NPU CANN 9.2.0 升级、以及 ROCm 镜像修复，表明项目正系统性地推进 NVIDIA 之外的硬件适配，与 README 强调的多后端定位一致。

**新模型与新特性**：kimi-k3 获得多条支持（在线 EPLB 专家重定位、MegaMoE 布局校验、PDL 时序修复），显示该模型是当前重点优化对象；rust-server 持续完善（预准入拒绝上报、launch core 分区保留），反映 API 层向 Rust 迁移的长期趋势。

## 3. 对项目的影响与潜在意义
- **稳定性提升**：修复集中在内存边界、并发锁、竞态条件，能显著降低生产环境偶发故障率。
- **硬件多元化**：AMD/NPU 的内核与文档更新降低用户迁移门槛，扩大部署覆盖面。
- **PD 分离（disaggregation）成熟度**：多条 disaggregation/PD 相关修复说明预填充-解码分离架构正走向生产可用。

## 4. 值得关注的技术点
- **Mooncake ranged get 带宽优化**：对大批次 KV 传输做范围限流，是 PD 分离场景下的实际性能改进。
- **Anima LayerNorm/timestep 融合**、**humming MoE prepare_buffers 主机开销降低**：图重放期算子融合是典型推理加速手段。
- **DCF top-k merge 扩展到 DCP 组 2/4**、**DSA split-K decode**：稀疏注意力路径的持续深挖。
- **函数调用流式处理**：修复一个 chunk 多个 tool call 与 InternLM 标记分割，提升 Agent 场景兼容性。
- **CI 安全实践**：HF 模型预取放在唯一持有 token 的可信步骤，体现供应链安全意识。

## 5. 对项目整体发展的影响
这些提交共同指向三个主线：**核心路径的健壮性打磨**（为大规模生产部署铺路）、**多模型多硬件的横向覆盖**（kimi-k3、AMD、NPU）、以及**基础设施工程化**（Rust server、CI 镜像、监控文档）。在 README 定位的"快速 LLM 与多模态推理"目标下，这批变更既非激进的功能扩张，也不是单纯修补，而是典型的成熟期项目质量深耕——通过大量边界修复和性能微优化累积可靠性与吞吐优势，同时借 CI/文档投入降低社区贡献与部署摩擦，巩固其作为主流推理框架的竞争地位。

## 详细提交记录

### [c4af57f](https://github.com/sgl-project/sglang/commit/c4af57ff93f301846fa1da4c31f8523c08c7510d)

- **作者**: Shaobo Zheng
- **时间**: 2026-11-25T23:58:22Z
- **提交信息**: [Fix] scheduler: Fix context-boundary max_new_tokens clipping (#33814)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [4a70f37](https://github.com/sgl-project/sglang/commit/4a70f3760be5f55ae18ecc12fa49aef63b91de01)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-25T23:46:30Z
- **提交信息**: [Fix] mem_cache: Size req_to_token rows from the per-decode allocation reach (#52926)

### [098d5e9](https://github.com/sgl-project/sglang/commit/098d5e9b1efd54f1aa180f630f96a9a045451626)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-25T23:45:32Z
- **提交信息**: [Fix] attention: Size per-request tables from the req_to_token row width (#53185)

### [2825eed](https://github.com/sgl-project/sglang/commit/2825eed88431a0ec98dda07bbd1fa96f8dfd7ad4)

- **作者**: aryatsc
- **时间**: 2026-11-25T23:44:31Z
- **提交信息**: [Fix] kimi-k3: Reject a MegaMoE expert layout DeepGEMM cannot hold when the model is built (#52948)

Co-authored-by: aryatsc <335164804+aryatsc@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [662ce8c](https://github.com/sgl-project/sglang/commit/662ce8c2dbc2992a7b003f466a7a37a05c965c1c)

- **作者**: YAMY
- **时间**: 2026-11-25T23:42:43Z
- **提交信息**: [Fix] kimi-k3: wait on the PDL primary before the first attention-residual bank load (#52627)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>

### [daa0aeb](https://github.com/sgl-project/sglang/commit/daa0aebbbfde030e2208deb7c05a3e3d0a2fbea4)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-25T23:03:33Z
- **提交信息**: [CI] pr-test: Prefetch each partition's Hugging Face models in a trusted step that alone holds the token (#53019)

### [3255a00](https://github.com/sgl-project/sglang/commit/3255a00b17c5de18d04cf7ca1c1d927d97dcf7d8)

- **作者**: llying-001
- **时间**: 2026-11-25T23:02:25Z
- **提交信息**: [Doc] [AMD] glm-5.2: PD disaggregation on MI355X with the Infera router (#52460)

Signed-off-by: liyingli <liyingli@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [a8fa697](https://github.com/sgl-project/sglang/commit/a8fa697343fd69f6746f0a79e8dd5c9aea279a17)

- **作者**: dorado269
- **时间**: 2026-11-25T22:45:24Z
- **提交信息**: [Doc] [AMD] cookbook: Muse Spark Open MI355X HiCache frees out-of-window SWA slots (#51760)

Signed-off-by: yihou <yihou@amd.com>

### [8b122e2](https://github.com/sgl-project/sglang/commit/8b122e2e5b46e417d9d233a2cd9b61ebc465708f)

- **作者**: Shangming Cai
- **时间**: 2026-11-25T22:25:08Z
- **提交信息**: [Fix] disaggregation: Hold the status lock while clear() pops a room (#53037)

### [216bd33](https://github.com/sgl-project/sglang/commit/216bd3357416a1039230227e2c9e1eec3869f0b7)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-25T22:08:43Z
- **提交信息**: [CI] mem_cache: Count the multicast gather copies as enqueued instead of profiled (#53132)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1a6164a](https://github.com/sgl-project/sglang/commit/1a6164afdaa7a5738527475897c2391ec3453c7e)

- **作者**: metamergebot
- **时间**: 2026-11-25T21:38:08Z
- **提交信息**: [Fix] rust-server: Report pre-admission refusals of /generate to the generate hook (#52958)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [c40b005](https://github.com/sgl-project/sglang/commit/c40b0058d6f07bcbbcf6d7ed44e45535c602341c)

- **作者**: metamergebot
- **时间**: 2026-11-25T21:38:00Z
- **提交信息**: [Feat] rust-server: Keep the launch core partition on the server instance (#52969)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [a3f0bff](https://github.com/sgl-project/sglang/commit/a3f0bff5babfe18d3862e134449cd8fd11fcb84a)

- **作者**: Yuwei An
- **时间**: 2026-11-25T18:28:40Z
- **提交信息**: [Fix] kernel_plugins: Offer the hybrid target verify's rows, verify scratch and auxiliary taps again (#53150)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d3bc4d8](https://github.com/sgl-project/sglang/commit/d3bc4d8b0f63f0eee46bfa69e460073a00b04591)

- **作者**: Kevin Mi
- **时间**: 2026-11-25T16:04:39Z
- **提交信息**: [Feat] [AMD] inkling2: Add the MI35x norm, sconv and MTP kernels (#52728)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ad3a9a3](https://github.com/sgl-project/sglang/commit/ad3a9a36abc9e5eaeb2a85d7457833f015193d1f)

- **作者**: Kevin Mi
- **时间**: 2026-11-25T16:03:32Z
- **提交信息**: [Feat] [AMD] inkling2: Add the MI35x MoE routing and expert GEMM kernels (#52727)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [324668d](https://github.com/sgl-project/sglang/commit/324668d8d5b5cabc4024842a5d5f80f56061d116)

- **作者**: Kevin Mi
- **时间**: 2026-11-25T15:27:36Z
- **提交信息**: [Feat] [AMD] inkling2: Add the MI35x attention kernels (#52726)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9041bbc](https://github.com/sgl-project/sglang/commit/9041bbcee8967ebed686500e72b95387b6624b52)

- **作者**: Erik Wijmans
- **时间**: 2026-11-25T15:17:36Z
- **提交信息**: [Fix] nemotron_h: Expose the pipeline stage's layer range (#52949)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [e6fe9be](https://github.com/sgl-project/sglang/commit/e6fe9be9476523b07eec70ac6bdbe77b5782f934)

- **作者**: DarkSharpness
- **时间**: 2026-11-25T14:28:58Z
- **提交信息**: [Fix] dsa: Drop the stale act_quant argument from the KPool skip-logits K-cache fill (#53107)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0ebfaa3](https://github.com/sgl-project/sglang/commit/0ebfaa356c7b93616d2d746655c67cf22b583de7)

- **作者**: Shuwen Wang
- **时间**: 2026-11-25T13:17:48Z
- **提交信息**: [Perf] linker: Bound the ranges per Mooncake ranged get so large load batches keep their bandwidth (#52906)

### [2005571](https://github.com/sgl-project/sglang/commit/2005571ac14aba66530a92e79c4e1e9883a2850c)

- **作者**: ishandhanani
- **时间**: 2026-11-25T12:25:01Z
- **提交信息**: [Doc] skills: Add the commit-approval, fork-approval, and rebase gates to babysit-pr-to-pass-ci (#53109)

### [b5519ce](https://github.com/sgl-project/sglang/commit/b5519ceb65a9d4d4141aa177d9f8824f8b58847f)

- **作者**: Shuwen Wang
- **时间**: 2026-11-25T12:04:00Z
- **提交信息**: [Fix] gdn: Initialize ReplaySSM verify stages in direct-commit test (#53077)

### [17bbb10](https://github.com/sgl-project/sglang/commit/17bbb10cb902339983efbf43d3e636f104b97610)

- **作者**: amote-i
- **时间**: 2026-11-25T11:57:17Z
- **提交信息**: [Doc] [NPU] docs: upgrade the supported CANN version to 9.2.0 (#52567)

### [0fde035](https://github.com/sgl-project/sglang/commit/0fde0356cc44bca9a7727a3a2e2c2d10cd5bd30f)

- **作者**: Khoa Pham
- **时间**: 2026-11-25T09:59:58Z
- **提交信息**: [Feat] kimi-k3: Support online EPLB expert relocation (#53050)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [b87ff3f](https://github.com/sgl-project/sglang/commit/b87ff3fe0ca2de33ec7694293e44ca673181aabc)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-25T09:28:37Z
- **提交信息**: [Doc] cookbook: Update Ling-3.2-air MTP benchmarks (#53082)

### [173f27f](https://github.com/sgl-project/sglang/commit/173f27ff8fd6e95f6d9ed65a52eea170bdec77a4)

- **作者**: Clint
- **时间**: 2026-11-25T08:47:33Z
- **提交信息**: [Fix] [AMD] docker: Use a ROCm 10.0 Triton build that fixes masked loads into LDS (#52641)

### [124c741](https://github.com/sgl-project/sglang/commit/124c741c8c479b656bdde2fe0b8438c0f8645eea)

- **作者**: Khoa Pham
- **时间**: 2026-11-25T08:42:18Z
- **提交信息**: [Perf] [NVIDIA] DSA: Enable DCP top-k merge for DCP groups of 2 and 4 (#53024)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [8a834e3](https://github.com/sgl-project/sglang/commit/8a834e3b274f8e3e0588b8f2d63d15d42ad7f8ae)

- **作者**: 黄孝君
- **时间**: 2026-11-25T08:42:04Z
- **提交信息**: [CI] [NPU] docker: Bump CANN to 9.2.0 and NPU kernel to 2026.11.0.post14 (#51818)

### [b323e8e](https://github.com/sgl-project/sglang/commit/b323e8e6e3aacfe606b11a2ef51ae73bc8b283a7)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-25T08:00:43Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main ad39ddd2 (#53052)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2ab8170](https://github.com/sgl-project/sglang/commit/2ab817031e3b0337217497dbc2c1d75eeacaaac0)

- **作者**: amote-i
- **时间**: 2026-11-25T07:56:03Z
- **提交信息**: [Doc] [NPU] docs: use Ascend Docker Runtime for the container commands (#52988)

### [5426e0e](https://github.com/sgl-project/sglang/commit/5426e0ef3bcfd1d6803babb15000b1ec6be9150c)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-25T07:09:40Z
- **提交信息**: [CI] diffusion: Run test_flashinfer_fa2_attention in the kernel-unit lane (#52908)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1890a5f](https://github.com/sgl-project/sglang/commit/1890a5fc62ed4f9fdeaf9bce24f8f8b241b508de)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-25T07:07:57Z
- **提交信息**: [Perf] Diffusion: Fuse Anima LayerNorm and timestep modulation during graph replay (#52897)

### [0b56532](https://github.com/sgl-project/sglang/commit/0b56532a03e3dac6d4607e8400ece4550d3b87d9)

- **作者**: 渺如星辰
- **时间**: 2026-11-25T06:53:43Z
- **提交信息**: [Perf] moe/humming: Reduce host overhead in prepare_buffers (#51885)

Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: ZD-zhu <1908144107@qq.com>

### [f7fbae1](https://github.com/sgl-project/sglang/commit/f7fbae17ce7f1f3c90f806a26d2a33623e021917)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-25T06:47:06Z
- **提交信息**: [Fix] hunyuan_v4_flash: Stop IndexPool kernels from compiling per batch shape (#52747)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [075925a](https://github.com/sgl-project/sglang/commit/075925a10f767ca464be068019d50955f42f6e30)

- **作者**: leon
- **时间**: 2026-11-25T06:46:31Z
- **提交信息**: [Perf] kimi-k3: Extend deferred-finalize push AR+RMSNorm window to 2 MB (M <= 292) (#52776)

### [b1ef3a6](https://github.com/sgl-project/sglang/commit/b1ef3a60797aa6c29bcfa4cc3bc135dd2f19ec22)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-25T06:30:58Z
- **提交信息**: [Refactor] models: Fix silent failures and prune dead code in srt models and layers (2/4) (#50804)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [661d9b3](https://github.com/sgl-project/sglang/commit/661d9b3fb4005d622c8fcbb919281f5221fed540)

- **作者**: Shunkangz
- **时间**: 2026-11-25T06:17:13Z
- **提交信息**: [Perf] HiSparse: optimize the swap in copy kerne (#51506)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [33731cd](https://github.com/sgl-project/sglang/commit/33731cdde7397e1883cf13a6febf4a53d42ccd42)

- **作者**: Sohom chakraborty
- **时间**: 2026-11-25T06:02:51Z
- **提交信息**: [Feat] sgl-router: Reject gateway-only flags with their replacement (#50643)

Signed-off-by: Sohom Chakraborty <16609933+sohom-cs@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [43a0456](https://github.com/sgl-project/sglang/commit/43a04561c77e0fe09e66c3528f7fdc7b58396d13)

- **作者**: Shangming Cai
- **时间**: 2026-11-25T06:02:26Z
- **提交信息**: [Fix] disaggregation: Make update_status's read-modify-write atomic (#52976)

### [75ed36d](https://github.com/sgl-project/sglang/commit/75ed36d976113c693f8e6f64925e119573a93fda)

- **作者**: ChihTsungLu
- **时间**: 2026-11-25T05:48:15Z
- **提交信息**: [Test] openai: Check malformed requests to /generate and OpenAI routes get a 4xx (#50753)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [5f241eb](https://github.com/sgl-project/sglang/commit/5f241eb8ba6cb43b5dde2d0e57f3ab1c482202ef)

- **作者**: dorado269
- **时间**: 2026-11-25T05:25:07Z
- **提交信息**: [Perf] [AMD] dsa: gfx950 split-K decode plan for 64-head fp8 sparse MLA (#47278)

Signed-off-by: yihou <yihou@amd.com>

### [5b4ddbb](https://github.com/sgl-project/sglang/commit/5b4ddbb609e9a6101e8c3620d22ade2059f77b62)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-25T04:58:52Z
- **提交信息**: [Fix] [AMD] docker: Pin apache-tvm-ffi==0.1.11 in ROCm image for xgrammar 0.2.9 (#52873)

Co-authored-by: Dhruv Singal <dhruvsingalabc@gmail.com>

### [8fdaa87](https://github.com/sgl-project/sglang/commit/8fdaa8787b264d09eee3b7e1dd64edaff1b9674b)

- **作者**: Jae B.
- **时间**: 2026-11-25T03:56:13Z
- **提交信息**: [Fix] pd: Keep a drained transfer Success when an abort lands late (#52654)

### [159790e](https://github.com/sgl-project/sglang/commit/159790ea33f0322ca0a3c23468ac59bbfb63a59d)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-25T03:34:14Z
- **提交信息**: [CI] rerun-test: Stop sourcing a 5090 profile that some runners no longer have (#52990)

### [1114f76](https://github.com/sgl-project/sglang/commit/1114f763d89f6511eed5f3a7f5264fb3f3996c19)

- **作者**: Sage
- **时间**: 2026-11-25T03:30:41Z
- **提交信息**: [Refactor] router: align Generate forwarding with the rust server API (#45808)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [c40aeba](https://github.com/sgl-project/sglang/commit/c40aeba2e061b6c4f8974cbcc67fc2721f445107)

- **作者**: ZY Y
- **时间**: 2026-11-25T03:15:26Z
- **提交信息**: [Test] [NPU] test: Lower the DSV4-Pro W4A8 L2 hit-rate GSP input to 28k to fit the prefill KV pool (#52970)

### [c673b0a](https://github.com/sgl-project/sglang/commit/c673b0ab5aab851cce963ece768772bb4794232e)

- **作者**: HeYao
- **时间**: 2026-11-25T03:10:43Z
- **提交信息**: [CI] [NPU] Dsv4-Flash: disable mix-chunk and re-enable DSPARK speculative inference (#52975)

Co-authored-by: HeYao <heyao@example.com>

### [67b09d1](https://github.com/sgl-project/sglang/commit/67b09d1c0ddd376e6ea5b9027ab42cf1b375305d)

- **作者**: Shangming Cai
- **时间**: 2026-11-25T03:05:47Z
- **提交信息**: [Fix] mooncake: Fall back to egm_numa_nodes="auto" when the GPU NUMA probe raises (#52947)

### [2805327](https://github.com/sgl-project/sglang/commit/28053272d979d9b27c64cd1b48cac26b68dff83b)

- **作者**: amote-i
- **时间**: 2026-11-25T02:06:20Z
- **提交信息**: [Doc] [NPU] docs: restore frozen image versions in ascend-npus (#52851)

### [90e7a34](https://github.com/sgl-project/sglang/commit/90e7a34b279393be1f1f74e66839bc3c86f9354e)

- **作者**: em-dreyer
- **时间**: 2026-11-25T01:53:01Z
- **提交信息**: [CI] docker: Publish a CUDA CI job container image to lmsysorg/sglang-ci (#51609)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [b9df1cd](https://github.com/sgl-project/sglang/commit/b9df1cd4b14c5aa76a44d92bfb8fb2bc627ccb87)

- **作者**: Haojie Song
- **时间**: 2026-11-25T01:48:35Z
- **提交信息**: [Fix] speculative: Reject unsupported DFLASH and DSpark step counts (#50299)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [5fe2260](https://github.com/sgl-project/sglang/commit/5fe2260893cbd95b9ecef258d0edc3026959e6f2)

- **作者**: Ruilin Gao
- **时间**: 2026-11-25T01:43:53Z
- **提交信息**: [Doc] diffusion/wan2.2: Load the high/low-noise LoRA files per expert in the cookbook example (#51484)

### [30a3796](https://github.com/sgl-project/sglang/commit/30a3796ca815e7b7c33636f44d3378af12b37deb)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-25T01:07:19Z
- **提交信息**: [Fix] function_call: Keep a split InternLM start marker after the first call (#52952)

Co-authored-by: sinksilk <785976238@qq.com>

### [b28fff2](https://github.com/sgl-project/sglang/commit/b28fff257ed7a1c615c2197e6491868fcd723355)

- **作者**: Sage
- **时间**: 2026-11-25T00:46:28Z
- **提交信息**: [Chore] sgl-router: decouple preprocessing from app state (#47959)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5ceb14e](https://github.com/sgl-project/sglang/commit/5ceb14e1adb8294fcf15cf527338cbeef92acbf4)

- **作者**: Yibo Liu
- **时间**: 2026-11-25T00:39:26Z
- **提交信息**: [Fix] function_call: Process every complete tool call in a streamed chunk (#50615)

Signed-off-by: Yibo Liu <yibol9768@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [357c4b6](https://github.com/sgl-project/sglang/commit/357c4b639db30011bdbbb81969aa81fd3d7d6690)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-25T00:31:22Z
- **提交信息**: [Doc] monitoring: Keep the Grafana password in .env and change it in place (#52924)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-25T20:51:32Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 2
- **主要提交者**: Butterfingrz, DefTruth

## AI分析总结

## 昨日提交分析总结（vipshop/cache-dit，#1400–#1409）

### 1. 主要更新类型

- **性能优化（主导）**：FP8/FP6 量化通信算子优化与 QKV 融合。
- **功能新增**：FP4 通信量化、分组 FP8/FP6 量化、UAA 融合 QKV 一次 all-to-all。
- **Bug 修复**：Ray 场景下 factory offload 状态丢失问题。
- **文档更新**：README 并行性章节重写（含 CP、3D-P 修正与排版）。

### 2. 关键变更点及与项目方向的关系

- **通信量化全谱系成型**：从 FP8（per-token、per-group-16/32）→ FP6（E2M3 打包算子）→ FP4，逐步补齐，直接对应 README 中"Quantization + Parallelism"两大核心卖点，目标是把 Ulysses all-to-all 的带宽/精度开销压到最低。
- **QKV 融合与调度分层**：新增 UAA 融合 QKV mega quant/dequant（一次 all-to-all 完成），同时保留标准调度与 mixed-K/GQA 回退路径——在极限优化与通用兼容之间做了稳妥权衡，契合"PyTorch 原生、开箱可用"的定位。
- **量化策略统一**：通信量化配置与 CLI 统一化，默认量化 K、显式 BF16 退出，降低用户配置成本，属于面向工程化的收敛性重构。
- **Ray + CPU Offload 修复**：保证分布式推理下 offload 工厂逻辑正确，呼应 README 的"CPU Offload"能力。
- **README 修订**：补齐 CP（Context Parallel）说明，使文档与实际并行能力对齐。

### 3. 影响与潜在意义

- 通信量化从实验性功能演进为**多精度、可配置、带性能背书**（含算子与 NCCL 测试记录）的完整子系统，显著提升大规模并行推理的吞吐上限。
- 量化默认策略（K 默认量化、BF16 显式退出）与配置统一，预示项目正从"研究原型"向"可产品化引擎"演进。
- Ray offload 修复提升分布式场景稳定性，降低实际部署风险。

### 4. 值得关注的技术点

- **D=128 多行与 per-token 单次读取量化路径**：减少量化 kernel 的访存次数，是典型带宽瓶颈优化手法。
- **FP6 E2M3 打包算子 + ulysses_fN 分发**：非常规精度的高效实现，体现底层 kernel 工程深度。
- **UAA 融合 QKV 一次 all-to-all**：将量化/反量化与通信融合，减少通信启动次数，是通信-计算融合的关键优化。
- **混合 K/GQA 回退机制**：GQA/MQA 异构 head 结构下的兼容处理，工程细节考究。
- 提交附带**性能数据与 NCCL 算子测试**，可复现性强，质量门槛较高。

### 5. 对项目发展的影响

结合 README——cache-dit 是面向 DiT 推理的 PyTorch 原生引擎，涵盖缓存、并行、量化与 CPU offload——这批提交表明项目当前重心正聚焦于**Ulysses 并行下的通信量化这一高价值瓶颈**：通过 FP8/FP6/FP4 全精度谱系、融合通信算子与统一配置，系统性地将并行通信开销压降，同时用 Ray offload 修复和 README 更新巩固分布式可用性与文档可信度。总体而言，项目正沿"性能纵深 + 工程成熟度"双轨推进，为后续更高精度（如 FP4 量产化）与更大规模并行部署奠定基础，这些优化使 cache-dit 在 DiT 推理性能竞争中保持差异化优势。

## 详细提交记录

### [332c677](https://github.com/vipshop/cache-dit/commit/332c6778eb4b74e7981b4f4ecc6006d6d9c04bcf)

- **作者**: DefTruth
- **时间**: 2026-11-25T15:59:03Z
- **提交信息**: feat(ulysses): add FP4 communication quantization (#1409)

### [0733f32](https://github.com/vipshop/cache-dit/commit/0733f32466ebbc89907dca18b2319dfc0d909d7f)

- **作者**: DefTruth
- **时间**: 2026-11-25T14:02:20Z
- **提交信息**: perf(ulysses): optimize FP8/FP6 QKV communication (#1407)

- Add D=128 multirow and per-token single-read quant paths.
- Optimize FP8/FP6 QKV/O quant and O dequant kernels.
- Add UAA fused QKV mega quant/dequant with one all-to-all.
- Preserve separate standard scheduling and mixed-K/GQA fallbacks.
- Record performance results and operator/NCCL tests.

### [3b35cbd](https://github.com/vipshop/cache-dit/commit/3b35cbdbdcea3403db600662e35f3997a1475145)

- **作者**: Butterfingrz
- **时间**: 2026-11-25T09:48:19Z
- **提交信息**: fix(ray): preserve factory offload (#1403)

Signed-off-by: Butterfingrz <13524387014@163.com>

### [f00329a](https://github.com/vipshop/cache-dit/commit/f00329a0400ac2f3d76ae60af0835b583513c943)

- **作者**: DefTruth
- **时间**: 2026-11-25T08:53:27Z
- **提交信息**: feat(ulysses): add grouped FP8/FP6 communication quantization (#1402)

- Add FP8 per-group-16/32 communication quantization.
- Add packed FP6 E2M3 operators and ulysses_fN dispatch.
- Unify communication quantization config and CLI.
- Quantize K by default with explicit BF16 opt-out.
- Document kernel, fused QKV, and second-level scale optimization roadmaps.

### [4048690](https://github.com/vipshop/cache-dit/commit/4048690c6c062d8a906a4e5e252ec0fb5d667362)

- **作者**: DefTruth
- **时间**: 2026-11-25T02:39:09Z
- **提交信息**: Update README.md (#1400)

* Update README.md

* Update README.md

* Fix formatting in README.md for Cache-DiT description

* Update README.md

* Revise README for Cache-DiT parallelism details

Updated the parallelism section in the README to include CP.

* Update README.md

* Update README.md

* Fix typo in Cache-DiT description

* Fix parallelism description in README

Updated the parallelism section in the README to correct '3D-P' to '3D-P'.

* Update README.md

* Update README.md

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97581
- **最后更新**: 2026-11-26T03:50:42Z

## 提交统计

- **昨日提交总数**: 83
- **提交者数量**: 61
- **主要提交者**: Juan Pérez de Algaba, Thien Tran, Bo Pang

## AI分析总结

# vLLM 昨日提交总结（共 83 个提交）

## 一、主要更新类型

- **性能优化占比最高**：包括 FlashInfer/FlashKDA/SM10x 内核调优、Nemotron/Kimi 专项加速、MoE 与 GEMM 优化、采样与卷积内核融合。
- **硬件平台扩展**：Intel XPU 与 AMD ROCm 各获约 6 项投入，合计接近半数。
- **Bug 修复约 20 项**：涉及多模态、ROCm、KV Offload、前端、Tokenizer、EC 外部计算等。
- **新特性**：Rust 前端指标导出、encoder cache 事件、DP-attention 支持、迭代指标工作负载快照、PP 请求准入策略改进、KVConnector 跨平台支持。
- **重构与工程**：移除 Mamba1 与 TeleFLM、KV cache 规划简化、SleepMode 钩子化、mypy 补全、构建体积控制与 CI 优化。

## 二、关键变更与项目方向

- **稀疏注意力与 MLA 是主线**：HiSparse 支持 FlashInfer SM90、SM90 NoPE sparse MLA 启用 ShardQ、滑窗 MLA 支持 fp8 DS KV cache，直接降低显存与计算开销。
- **Transformers 后端持续深化**：MoE 融合、ROCm AITER shared experts、权重键名迁移等多笔提交，旨在打造统一的模型接入路径。
- **Rust 前端成熟化**：补齐 preemptions、NIXL、KV offload 指标，以及队列限额、日志回显、类型化 flag 与编译因子解耦。
- **分布式与 KV 体系**：NIXL 共享主机 KV、MoRIIO 读写修复、Mooncake KV connector 修复、KV offload 共享与调度改进。
- **平台多元化**：ROCm（MoRIIO、AITER W4A16、gfx950 单内核 top-k）、XPU（LoRA GEMM、Triton MLA、MXFP4 MoE LoRA）持续补齐。

## 三、项目影响与潜在意义

内核级优化与稀疏/低比特支持将直接提升吞吐、降低单请求成本；Transformers 后端与 Rust 前端双线推进，分别降低模型接入门槛、提升服务稳定性；XPU/ROCm 深度投入兑现 "for everyone" 的跨硬件愿景；针对 DeepSeek、MiniMax、Muse Spark 等热门模型的专项优化保持前沿首发能力；大量并发修复与代码清理提升生产可靠性，降低维护成本。

## 四、值得关注的技术点

- **PP 空闲步准入**：允许空闲步后接纳新请求并从积压队列规划 prefill microbatch，可能显著降低高负载排队延迟。
- **多模态视觉 FA3 批不变性修复**：对确定性推理和回归测试意义重大。
- **GDN prefill 因果卷积与后处理融合**为单一 CUDA 内核，体现长序列场景的融合收益。
- **Nemotron Shortcut 按 key position 一次性转换 NVFP4 K/V**，是低比特 KV 的巧妙工程实践。
- **Rust 前端编译因子解耦**：减少不必要的重编译，对大型组件意义明显。
- GLM/Kimi 的 chunked prefill 专项内核持续压榨长上下文性能；Qwen4Exp 主机端暂存 PLE 行拓展受限硬件可运行性。
- 多笔提交出现 Claude、Codex、vllm-agent 等 AI 署名，反映 AI 辅助开发已深度融入该仓库工作流。

## 五、整体评价

README 定位是"人人可用的快速、低成本 LLM 服务"。本日提交从三个层面推进该目标：**性能层**通过稀疏注意力、低比特 KV 与平台内核优化降本增延迟；**易用层**通过 Transformers 后端统一接入与多硬件支持降低门槛；**可靠性层**通过 Rust 前端指标、KV 体系修复与工程清理保障生产稳定。vLLM 正处于"多硬件并行 + 内核极限优化 + 工程精细化"的成熟迭代期，从"能跑"向"跑得省、跑得稳、接得快"的推理基础设施持续演进。

## 详细提交记录

### [ed686cc](https://github.com/vllm-project/vllm/commit/ed686ccec527b48de4c8a67927184933886f062a)

- **作者**: Ankit Raj
- **时间**: 2026-11-25T23:26:55Z
- **提交信息**: [Bugfix][HiSparse][NIXL] Import shared host KV on every node's host leader (#69901)

Signed-off-by: Ankit1478 <119005879+Ankit1478@users.noreply.github.com>

### [76433bb](https://github.com/vllm-project/vllm/commit/76433bbb307e4e27f0e40bd7979bb8750588840d)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-25T23:03:12Z
- **提交信息**: [HiSparse] Support the FlashInfer SM90 sparse MLA backend (#61277)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [49ab32c](https://github.com/vllm-project/vllm/commit/49ab32c35c6a33feb37a8a91195c41179f0dbd1b)

- **作者**: Simon Danielsson
- **时间**: 2026-11-25T22:41:26Z
- **提交信息**: [ROCm] Support DP-attention in AITER Triton W4A16 MoE (#66159)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>

### [0fbba2a](https://github.com/vllm-project/vllm/commit/0fbba2aa715eecf5d39b2a8c0b002553441321c1)

- **作者**: Hangrui Cao
- **时间**: 2026-11-25T22:01:09Z
- **提交信息**: [Bugfix][Multimodal] Make vision FA3 batch invariant (#69774)

Signed-off-by: Hangrui Cao <hangrui.cao@zoom.us>
Co-authored-by: Hangrui Cao <hangrui.cao@zoom.us>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [a588d39](https://github.com/vllm-project/vllm/commit/a588d3974e08fa0a614152ee6b62762f62777ed4)

- **作者**: Bolin Sun
- **时间**: 2026-11-25T21:46:11Z
- **提交信息**: [Perf][GLM-5.3-Flash] KDA: planar short conv for chunked prefill on SM10x (#66884)

Signed-off-by: Bolin Sun <bolins@nvidia.com>
Co-authored-by: Ao Tang <aot@nvidia.com>

### [72b87c8](https://github.com/vllm-project/vllm/commit/72b87c8867a0a0a73b1b7acb3b3fe3f317f517dd)

- **作者**: Luca Motz
- **时间**: 2026-11-25T21:43:01Z
- **提交信息**: [Transformers backend] Fix `model_impl="transformers"` for architectures Transformers doesn't have (#69955)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b40b2a9](https://github.com/vllm-project/vllm/commit/b40b2a99c09e780d6c3c22ef496e3b3ee002fa0c)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-25T21:23:29Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: serve the model card's sampling defaults; Kimi-K3 / K3.1-Pro: opt-in strict tool calls (#69624)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ebe4901](https://github.com/vllm-project/vllm/commit/ebe4901d02ea90b336ced8e2168820fb8a5c9da9)

- **作者**: Harry Mellor
- **时间**: 2026-11-25T20:52:10Z
- **提交信息**: [Transformers backend] Migrate A.X-K1 to the Transformers modeling backend (#67277)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [85a084c](https://github.com/vllm-project/vllm/commit/85a084c38c2c714c6fbdf0bdcd195b7f0301dece)

- **作者**: Cheng Rui
- **时间**: 2026-11-25T19:33:22Z
- **提交信息**: [Perf][Attention] Enable ShardQ for SM90 FlashInfer NoPE sparse MLA prefill (#69086)

Signed-off-by: Cheng Rui <286040359@qq.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8136afc](https://github.com/vllm-project/vllm/commit/8136afc2f82187cc60172e4c31315d4167497d79)

- **作者**: Vyomakesh
- **时间**: 2026-11-25T19:19:58Z
- **提交信息**: [Model] Remove TeleFLM (#69929)

Signed-off-by: vyomakesh0728 <dvyomkesh.vishwakarma@gmail.com>
Co-authored-by: Antigravity <noreply@google.com>

### [7b7af30](https://github.com/vllm-project/vllm/commit/7b7af30196ad3f12eadaa008fb3bf589ba02d520)

- **作者**: Harry Mellor
- **时间**: 2026-11-25T18:54:52Z
- **提交信息**: [Transformers backend] Splice the fused MoE into the MoE block's traced forward (#69868)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1542adb](https://github.com/vllm-project/vllm/commit/1542adb40fe442128ff7d8cf479550c8057e9d2b)

- **作者**: Vyomakesh
- **时间**: 2026-11-25T18:47:22Z
- **提交信息**: [Model] Decouple `nemotron_nas` from llama (#69726)

Signed-off-by: vyomakesh0728 <dvyomkesh.vishwakarma@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Antigravity <noreply@google.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b7186d1](https://github.com/vllm-project/vllm/commit/b7186d137addf271d4dd24c8d73c9985437baddc)

- **作者**: xinnywinne
- **时间**: 2026-11-25T18:31:43Z
- **提交信息**: [Frontend] Report time to first content token in per-request metrics (#56914)

Signed-off-by: wxin <wxin@nvidia.com>

### [83f120d](https://github.com/vllm-project/vllm/commit/83f120dcfcc101360c717bdfd8e40717ae8e7b1f)

- **作者**: kliuae
- **时间**: 2026-11-25T18:24:50Z
- **提交信息**: [Bugfix][ROCm][MoRIIO] Skip zeroing READ destinations and wait for their pending copies (#67074)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [aec644a](https://github.com/vllm-project/vllm/commit/aec644a8f9e7b8c6b962ee3fe02ba541fa9a430c)

- **作者**: TomerBN-Nvidia
- **时间**: 2026-11-25T16:48:39Z
- **提交信息**: [Bugfix][Nemotron Shortcut] Fix refits and match training video preprocessing (#69642)

Signed-off-by: tbarnatan <tbarnatan@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [94b13b3](https://github.com/vllm-project/vllm/commit/94b13b3d84562054f089e709ba1e32cf9a153bb7)

- **作者**: Misha Goin
- **时间**: 2026-11-25T16:28:04Z
- **提交信息**: [Perf][Kimi K3] Specialized decode: compile each kernel once, only for captured sizes (#69669)

### [e7f220f](https://github.com/vllm-project/vllm/commit/e7f220fdfaf71bb85d8c4bb833070101e9a6ced6)

- **作者**: Bo Pang
- **时间**: 2026-11-25T16:14:12Z
- **提交信息**: [Perf][Multimodal] Reduce Qwen3 audio encoder overhead (#69116)

Signed-off-by: Bo Pang <bopang314@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [c62590e](https://github.com/vllm-project/vllm/commit/c62590e002f2ec6c5ca4ce8bd3f6d8e1cd04547f)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T16:03:17Z
- **提交信息**: [Rust Frontend] Let the server run over any `Llm` (#64729)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5286bca](https://github.com/vllm-project/vllm/commit/5286bca05372488f530a2faf865ad6ef979d1a2c)

- **作者**: kliuae
- **时间**: 2026-11-25T15:56:53Z
- **提交信息**: [Bugfix][ROCm][MoRIIO] READ mode restore the cached recurrent state for hybrid prefixes that end on a block (#67216)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Claude Opus <noreply@anthropic.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [6e248ce](https://github.com/vllm-project/vllm/commit/6e248ce820abcd8e2760354a95cecf0a3a0f1225)

- **作者**: GuorongYe
- **时间**: 2026-11-25T15:24:40Z
- **提交信息**: [HY4 Flash] Allow fp8_ds_mla KV cache on Flash sliding-window MLA (#68365)

Signed-off-by: GuorongYe <35474918+grYe99@users.noreply.github.com>
Signed-off-by: grYe99 <guorongye99@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [c331ec8](https://github.com/vllm-project/vllm/commit/c331ec85faa6b1500f8650897cdbdf21d59e0b85)

- **作者**: Harry Mellor
- **时间**: 2026-11-25T15:19:20Z
- **提交信息**: [Bugfix][Transformers backend] Match ignored unexpected keys after renaming (#69918)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a95f173](https://github.com/vllm-project/vllm/commit/a95f173d5f0631499adfb3e4eb8b370d07eec4b0)

- **作者**: Aaron Pham
- **时间**: 2026-11-25T15:00:52Z
- **提交信息**: [Bugfix][NIXL] Tile whole kernel rows of groups to persist logical block for drafter blocks (#68742)

Signed-off-by: Aaron Pham <contact@aarnphm.xyz>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [fca34c0](https://github.com/vllm-project/vllm/commit/fca34c0a998fa6b58f98e1a06da08b77c5a78dd6)

- **作者**: Taneem Ibrahim
- **时间**: 2026-11-25T14:52:17Z
- **提交信息**: [Bugfix] Preserve Clef SystemOne probabilities with raw pooling outputs (#69329)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [0085fac](https://github.com/vllm-project/vllm/commit/0085facc58dedeef757aca3f51d6508e2ef9b148)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-25T13:58:53Z
- **提交信息**: [Model] Remove Mamba1 models and kernels (#68177)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [57906d3](https://github.com/vllm-project/vllm/commit/57906d3cc08e8dd9c73a92958ea53fbc6c5f8576)

- **作者**: waizuichougou
- **时间**: 2026-11-25T13:11:59Z
- **提交信息**: [Bugfix][Frontend] Refresh echoed text after prompt truncation (#62691)

Signed-off-by: waizuichougou <2082431897@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [99d66ff](https://github.com/vllm-project/vllm/commit/99d66fffac23a3ab5d78f2b8c47b3a91985cda8f)

- **作者**: danielafrimi
- **时间**: 2026-11-25T12:38:27Z
- **提交信息**: [Perf][Model] Nemotron Shortcut SDSA: convert NVFP4 K/V once per request by key position (#69738)

Signed-off-by: Daniel Afrimi <dafrimi@nvidia.com>
Co-authored-by: amitz-nv <203509407+amitz-nv@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [689b84c](https://github.com/vllm-project/vllm/commit/689b84c3697623552c0a11eb1e348bf32bc31bba)

- **作者**: Harry Mellor
- **时间**: 2026-11-25T11:52:24Z
- **提交信息**: [Transformers backend] Support ROCm AITER fused shared experts (#67283)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [46042d7](https://github.com/vllm-project/vllm/commit/46042d710e9d46ffda0402f8d54814870bccf296)

- **作者**: wzrd
- **时间**: 2026-11-25T11:19:39Z
- **提交信息**: [Refactor][SleepMode] Make the allocator data copy a subclass hook (#69828)

Signed-off-by: wzrd <floatlibai@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7aa7b78](https://github.com/vllm-project/vllm/commit/7aa7b7898170826ea07a326e255637aa4d7b8f17)

- **作者**: ntu-b12505041
- **时间**: 2026-11-25T11:06:52Z
- **提交信息**: [MyPy] Complete kv-C and enforce KV connector tests (#63008)

Signed-off-by: ntu-b12505041 <201773904+ntu-b12505041@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: ntu-b12505041 <201773904+ntu-b12505041@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f1c9dd7](https://github.com/vllm-project/vllm/commit/f1c9dd79cf6db0079cced6536eebecf6e58ae503)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T10:43:08Z
- **提交信息**: [Rust Frontend] Cap Qwen3-VL videos at 32 per prompt by default (#69864)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0cd313c](https://github.com/vllm-project/vllm/commit/0cd313c243e93da42450e94170450b6233d5e2e7)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T10:42:11Z
- **提交信息**: [Rust Frontend] Echo null logprobs for prompt tokens the engine never scored (#69865)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0d11e65](https://github.com/vllm-project/vllm/commit/0d11e65f6a2dfbb65426c6d585b1456d829eecf8)

- **作者**: Devanshi Jain
- **时间**: 2026-11-25T10:41:58Z
- **提交信息**: [Docs] keep the prompt prefix cacheable in agent workloads (#66683)

Signed-off-by: Devanshi Jain <devanshijain@meta.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9bf883b](https://github.com/vllm-project/vllm/commit/9bf883b8c2042df6365fd424af12fb1c5a79cf8e)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T10:39:43Z
- **提交信息**: [Rust Frontend] Export vllm:nixl_num_declined_expired_reads (#69863)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ab388dc](https://github.com/vllm-project/vllm/commit/ab388dc5b15280f9815fba2eeaa9c81844e5857b)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T10:38:43Z
- **提交信息**: [Rust Frontend] Count vllm:num_preemptions from scheduler stats (#69862)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [499f920](https://github.com/vllm-project/vllm/commit/499f92046043fe849c1f30585178e5e688f48acb)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T10:37:44Z
- **提交信息**: [Rust Frontend] Export OffloadingConnector KV offload metrics (#69848)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e83c9da](https://github.com/vllm-project/vllm/commit/e83c9daa25a7fb630251c2e966c9246a6ff88faf)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-11-25T10:26:12Z
- **提交信息**: [ROCm][DSv4.1] Score the sparse-indexer prefill on ShardQ token slices (#65555)

Signed-off-by: AMD-yanfeiwang <yanfei.wang@amd.com>
Signed-off-by: Yanfei Wang <yanfei.wang@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3332daf](https://github.com/vllm-project/vllm/commit/3332daf8fe613c0e3d7c06f42b12e95eb450aa1e)

- **作者**: Thien Tran
- **时间**: 2026-11-25T09:58:41Z
- **提交信息**: [Kernel] Bump FlashKDA to a32181e (codegen opts + 132→9 variant pruning) (#69787)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e5fb194](https://github.com/vllm-project/vllm/commit/e5fb19408db2ab9e584464399d64c88fe6916459)

- **作者**: Anjie Hou
- **时间**: 2026-11-25T09:41:04Z
- **提交信息**: [Bugfix][MRV2] Align CUDA graph capture input_ids and inputs_embeds with execute_model (#69795)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Antigravity <noreply@google.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5a8940b](https://github.com/vllm-project/vllm/commit/5a8940b999d29ec39e56fd95ccdf037fbdba9e46)

- **作者**: GuorongYe
- **时间**: 2026-11-25T09:28:28Z
- **提交信息**: [Model] Enable data-parallel multimodal encoder for HY4 (#69676)

Signed-off-by: grYe99 <guorongye99@gmail.com>
Signed-off-by: GuorongYe <565627635@qq.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [e979fc3](https://github.com/vllm-project/vllm/commit/e979fc349fb52df343fc110f4502146f36873a47)

- **作者**: milesial
- **时间**: 2026-11-25T09:28:07Z
- **提交信息**: [Bugfix][Multimodal] Nemotron 3.5 Super VL: size video frames from the image processor config (#68776)

Signed-off-by: Alexandre Milesi <milesial@users.noreply.github.com>
Signed-off-by: milesial <milesial@users.noreply.github.com>

### [93873e7](https://github.com/vllm-project/vllm/commit/93873e7aca8765abf83524e27a56fac638326104)

- **作者**: Yuki Kitaya
- **时间**: 2026-11-25T09:16:25Z
- **提交信息**: [Model] Qwen4Exp: stage CPU-offloaded PLE rows on the host when UVA is unavailable (#62847)

Signed-off-by: Yuki Kitaya <72787572+yeighta@users.noreply.github.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [ace48d8](https://github.com/vllm-project/vllm/commit/ace48d894c74fd2580897abdba90359d7429ae0e)

- **作者**: Guancheng Fu
- **时间**: 2026-11-25T09:13:47Z
- **提交信息**: [XPU][LoRA] Use dense GEMM for single-adapter prefill batches (#66752)

Signed-off-by: Guancheng Fu <guancheng.fu@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [eabbade](https://github.com/vllm-project/vllm/commit/eabbade5746104ba792916933499008b7f4e7330)

- **作者**: Bandham Manikanta
- **时间**: 2026-11-25T09:13:11Z
- **提交信息**: [Bugfix][Tokenizer] Route skip_special_tokens=False through Tekken byte fallback (#67755) (#67814)

Signed-off-by: Manikanta Bandham <bandhammanikanta@gmail.com>
Signed-off-by: Manikanta Bandham <bandham.manikanta@gmail.com>
Signed-off-by: Bandham Manikanta <bandhammanikanta@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d619466](https://github.com/vllm-project/vllm/commit/d6194665679ba4d8e3062cb1b409e8f1136aa22a)

- **作者**: Itay Etelis
- **时间**: 2026-11-25T09:10:16Z
- **提交信息**: [KV Offload] Share replicated MLA KV per host (#69677)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [27053d0](https://github.com/vllm-project/vllm/commit/27053d0137005f5d5e55077314fa40d22b16d7fb)

- **作者**: sssqqeer
- **时间**: 2026-11-25T09:09:17Z
- **提交信息**: [KV Offload] Return pending work, events and stats from on_schedule_end (#68962)

Signed-off-by: shibin <306219114@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dd08385](https://github.com/vllm-project/vllm/commit/dd08385536adb5a750ab51b7b9406adbf4aec14d)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-25T08:58:08Z
- **提交信息**: [Core] Simplify KV cache planning (#69814)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Antigravity <noreply@google.com>

### [9e8b3fb](https://github.com/vllm-project/vllm/commit/9e8b3fb83ed4f3da1ed5376083027b14994939fc)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-25T08:15:26Z
- **提交信息**: [XPU][CI] Enable v1/engine tests on XPU (#66926)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8b3b9ad](https://github.com/vllm-project/vllm/commit/8b3b9ad98cc93263e10776f67767d7a1af4fdf64)

- **作者**: Yicong Wang
- **时间**: 2026-11-25T08:05:33Z
- **提交信息**: [Bugfix][KV Connector][Mooncake] Keep extensible KV with RDMA-capable peermem allocations (#68357)

Signed-off-by: wangyicong <wangyicong@bytedance.com>
Co-authored-by: Codex <codex@openai.com>

### [2ca6af3](https://github.com/vllm-project/vllm/commit/2ca6af3c873595d6880dc15193f1790125845c95)

- **作者**: Tianyu Guo
- **时间**: 2026-11-25T07:57:17Z
- **提交信息**: [Bugfix][EC] Let Mooncake consumers encode requests without EC params locally (#69366)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [778bef2](https://github.com/vllm-project/vllm/commit/778bef285ad315ee347100f40f9d9285b4400f37)

- **作者**: Qiu Chunshuo
- **时间**: 2026-11-25T07:52:29Z
- **提交信息**: [Bugfix][Frontend] Account for PCP size in DP supervisor device_ids (#69664)

Signed-off-by: QiuChunshuo <chunshuoq@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5dda863](https://github.com/vllm-project/vllm/commit/5dda863a4b7dbc131ba3ec18d6fa85a58e096abf)

- **作者**: Dylan
- **时间**: 2026-11-25T07:47:45Z
- **提交信息**: [Rust Frontend] Enforce --max-num-queued-reqs and --max-num-queued-tokens (#69640)

Signed-off-by: Dylan Chen <dylan@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [08c497e](https://github.com/vllm-project/vllm/commit/08c497efa9a5213f2903670655f040977ba03fbd)

- **作者**: Tony Lin
- **时间**: 2026-11-25T07:25:55Z
- **提交信息**: [Bugfix][Bench] Fix KV cache planning for pipeline forwards (#69428)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [69d3af8](https://github.com/vllm-project/vllm/commit/69d3af837daa895239a930562629251271636a3f)

- **作者**: Artur Fierka
- **时间**: 2026-11-25T06:39:11Z
- **提交信息**: [Kernel][XPU] Tensor-descriptor Q loads in Triton MLA decode attention (#64881)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [acb8718](https://github.com/vllm-project/vllm/commit/acb87186fa011e273f2d77af4a0517664e2c35a2)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-25T06:31:21Z
- **提交信息**: [Bugfix][Kimi-K3] Render image and text parts in request order (#69584)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3c0c2c6](https://github.com/vllm-project/vllm/commit/3c0c2c6626ecedca4fdce6941918fcc642def541)

- **作者**: Johnson
- **时间**: 2026-11-25T06:28:07Z
- **提交信息**: [Perf] SM100/SM103 skinny GEMM plans for Qwen3, Qwen3.5/3.6 MoE and Qwen3.8 decode projections (#69736)

Signed-off-by: Johnsonms <lizhaofu@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cd43ca7](https://github.com/vllm-project/vllm/commit/cd43ca7804fa9c1fff6d691bb4274759ee66936f)

- **作者**: Anneketh Vij
- **时间**: 2026-11-25T06:27:47Z
- **提交信息**: [Bugfix] Align AFMoE BF16 router precision with Transformers (#68248)

Signed-off-by: Anneketh Vij <142443606+annekethvij@users.noreply.github.com>

### [3a67a05](https://github.com/vllm-project/vllm/commit/3a67a0570682bcb19a4527458d0680fd5074d11b)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T06:27:37Z
- **提交信息**: [Bugfix][Frontend] Allow only the Omni shared span among overlapping multimodal placeholders (#69604)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9b1d981](https://github.com/vllm-project/vllm/commit/9b1d98140f2a3a4d4b5bb841edc5a70401c3cb93)

- **作者**: Matt
- **时间**: 2026-11-25T06:22:29Z
- **提交信息**: [Spec Decode][ROCm][Muse Spark] FP8 DSpark draft through the speculative config (#67340)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Signed-off-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [bd05cc9](https://github.com/vllm-project/vllm/commit/bd05cc9bb93c0312c24f45b3f9e62c373e321554)

- **作者**: Isotr0py
- **时间**: 2026-11-25T06:08:33Z
- **提交信息**: [Bugfix] Fix duplicate kv quant mode int enum (#69816)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [c2cc003](https://github.com/vllm-project/vllm/commit/c2cc003c5b644095cabcd5212d2967546ce344f8)

- **作者**: my-git9
- **时间**: 2026-11-25T05:38:50Z
- **提交信息**: [Feature] Add encoder cache events (#67030)

Signed-off-by: xin.li <xin.li@daocloud.io>
Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Signed-off-by: my-git9 <xin.li@daocloud.io>
Co-authored-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d51a514](https://github.com/vllm-project/vllm/commit/d51a5147112a31dfbed08cfa4b774c27c34ce90d)

- **作者**: liuzhenwei
- **时间**: 2026-11-25T05:05:00Z
- **提交信息**: [XPU] Enable XPU graph mode for 6 recipes (#69605)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4768f92](https://github.com/vllm-project/vllm/commit/4768f921cdaf1df7583516582fafc7fb351ebee0)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-25T05:02:56Z
- **提交信息**: [Misc] Remove remaining xformers references (#69794)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b4edd5e](https://github.com/vllm-project/vllm/commit/b4edd5eb377808b07097c9e62bc9bd3a0cb68a4c)

- **作者**: Yan Ma
- **时间**: 2026-11-25T04:59:58Z
- **提交信息**: [XPU] add spec decode UT (#69653)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [249e652](https://github.com/vllm-project/vllm/commit/249e652909228b61bba2c409ca5ae6c84d236783)

- **作者**: Nick Hill
- **时间**: 2026-11-25T04:46:44Z
- **提交信息**: [Core][PP] Admit new requests past idle empty steps, and size prefill microbatches from the backlog (#68614)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3b0c94e](https://github.com/vllm-project/vllm/commit/3b0c94e6355458142d481d4a68a56461b00bf1ce)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-25T04:29:02Z
- **提交信息**: [XPU][LoRA] Support MXFP4 MoE LoRA via XpuFusedMoe hooks (#62631)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Signed-off-by: Chaojun,Zhang <chaojun.zhang@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8b847d4](https://github.com/vllm-project/vllm/commit/8b847d4a22182c8b5b3cbc9576126e0e71dcad92)

- **作者**: Hongkuan Zhou
- **时间**: 2026-11-25T04:09:46Z
- **提交信息**: [Feature] Add workload snapshots to iteration metrics (#61691)

Signed-off-by: hongkuanz <hongkuanz@nvidia.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [fa2f50f](https://github.com/vllm-project/vllm/commit/fa2f50f3fc227c3a45bec4a59ca8ebe9acabe98e)

- **作者**: rebel-eunji
- **时间**: 2026-11-25T04:08:35Z
- **提交信息**: [Bugfix][EC] Reuse runner cache hits before remote admission (#65079)

Signed-off-by: rebel-eunji <eunji.lee@rebellions.ai>
Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6d6875e](https://github.com/vllm-project/vllm/commit/6d6875ed930241d78d86d576aee85a0d9069468d)

- **作者**: zofia
- **时间**: 2026-11-25T03:58:53Z
- **提交信息**: [XPU] Flatten N-D input in XPU W8A16 FP8 linear kernel (#68308)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2afc637](https://github.com/vllm-project/vllm/commit/2afc637fb40a44b6b8dafab8e8d188f347cb2e6c)

- **作者**: David Zhu
- **时间**: 2026-11-25T03:57:43Z
- **提交信息**: [ROCm][Perf][DSv4.1] Use the single-kernel DSv4 top-k on ROCm gfx950 (#65742)

Signed-off-by: David Zhu <david.zhu@amd.com>
Co-authored-by: Hemanth Acharya <heachary@amd.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2d08d35](https://github.com/vllm-project/vllm/commit/2d08d35d4e6dddcbca029824253f15a627980ae5)

- **作者**: Thien Tran
- **时间**: 2026-11-25T03:32:04Z
- **提交信息**: [Perf][Kernel][GDN] Fuse the prefill causal conv1d + post-conv prep into one CUDA kernel (#69135)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: liusy58 <mg21330037@smail.nju.edu.cn>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5cc69fe](https://github.com/vllm-project/vllm/commit/5cc69fe699a27f5d8bc78da4bb9447bd59925836)

- **作者**: psv666
- **时间**: 2026-11-25T03:01:53Z
- **提交信息**: [Perf][Multimodal] Reuse OpenCV capture for video metadata (#66466)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ddcf64b](https://github.com/vllm-project/vllm/commit/ddcf64b36fa9251f805c8d3a85dcb9d0549670f0)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T02:38:26Z
- **提交信息**: [Rust Frontend] Exclude frontend and install-time env vars from compile factors (#69383)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [52c0c67](https://github.com/vllm-project/vllm/commit/52c0c67191c5271526909f907e1fe4362868d499)

- **作者**: Bugen Zhao
- **时间**: 2026-11-25T02:31:21Z
- **提交信息**: [Rust Frontend] Gate opt-in features at startup through typed flags (#68841)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [be29783](https://github.com/vllm-project/vllm/commit/be29783a314e600d3ff7bba44ac88d21b5adea89)

- **作者**: Harry Mellor
- **时间**: 2026-11-25T02:28:14Z
- **提交信息**: [Docs] Reduce docs build size below the Read the Docs limit (#69729)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e59fb18](https://github.com/vllm-project/vllm/commit/e59fb18b4ca1ef72c523ba20a1c9d0b78b13e747)

- **作者**: Vinayak Gokhale
- **时间**: 2026-11-25T02:21:07Z
- **提交信息**: [ROCm][MiniMax-M3.1] All gather in FP4 in TP configs (#67039)

Signed-off-by: Vinayak Gokhale <vinayak.gokhale@amd.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2f5d8a2](https://github.com/vllm-project/vllm/commit/2f5d8a2b144c0f1e90cae64084288c4039d6c0ce)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-25T02:15:35Z
- **提交信息**: [Security] Bound synchronous media body fetches (#69461)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6e3afdd](https://github.com/vllm-project/vllm/commit/6e3afdd5e68155f0092e6a6e6c837accf4f3eb2c)

- **作者**: Fanli Lin
- **时间**: 2026-11-25T01:58:14Z
- **提交信息**: [KVConnector] Enable HF3FS KV connector on non-CUDA devices (#66969)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [98e35c3](https://github.com/vllm-project/vllm/commit/98e35c3e09c001bfbc783d75415cd7feb553f152)

- **作者**: Matt
- **时间**: 2026-11-25T01:55:16Z
- **提交信息**: [ROCm][Muse Spark] Decode MoE on native routes (#67306)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [836a813](https://github.com/vllm-project/vllm/commit/836a8139988b5a2733a20e99d208b19e286cf6ad)

- **作者**: Matt
- **时间**: 2026-11-25T01:55:03Z
- **提交信息**: [ROCm][Spec Decode][Muse Spark] Fuse the DSpark Markov sampling steps (#67382)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Aliasger Zaidy <aliasger.zaidy@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [04f0149](https://github.com/vllm-project/vllm/commit/04f0149d472c28e6bf048c3f888b8112909ca973)

- **作者**: Wei-Cheng (Wayne) Chiu
- **时间**: 2026-11-25T01:54:31Z
- **提交信息**: [Bugfix][Rust Frontend] Bump fastokens to 0.3.6 (#66327)

Signed-off-by: WEI CHENG CHIU <waynehacking8@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [013ae19](https://github.com/vllm-project/vllm/commit/013ae19bf6db6dee63e875bbc06afa200bbe3a12)

- **作者**: Mike Garuccio
- **时间**: 2026-11-25T01:40:31Z
- **提交信息**: [Perf][XPU] Run the fp32 lm_head through torch.mm(out_dtype=float32) on XPU (#69186)

Signed-off-by: Mike Garuccio <mgaruccio@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2e53ef6](https://github.com/vllm-project/vllm/commit/2e53ef6cfd973601d23820624867185aaad24c64)

- **作者**: stefankoncarevic
- **时间**: 2026-11-25T01:36:01Z
- **提交信息**: [CI][ROCm][DSv4.1] Pool 16 decode pairs at TP8 in the mono layers test (#69707)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b3bad87](https://github.com/vllm-project/vllm/commit/b3bad87eb137c6d2fedda152ff2d3e3df3a32952)

- **作者**: Thien Tran
- **时间**: 2026-11-25T00:47:36Z
- **提交信息**: [Kernel] Keep L1::no_allocate on CuTeDSL GEMM epilogue stores (#69698)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-26
**监控日期**: 2026-11-25
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7966
- **最后更新**: 2026-11-26T03:53:09Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 27
- **主要提交者**: noone-zhhh, Dominik Farhan, chenqi49

## AI分析总结

# vllm-omni 昨日提交分析（39 笔）

## 1. 主要更新类型

- **CI/构建（约 15 笔，占比最高）**：大量 ROCm/NIGHTLY 测试覆盖扩展与门控
- **性能优化（约 8 笔）**：扩散模型、TTS 内核编译、零拷贝通信
- **Bug 修复（约 10 笔）**：跨模型、跨硬件的正确性修复
- **功能新增（约 6 笔）**：流式输入、批量化执行、流式 API 协议
- 少量重构与测试完善

## 2. 关键变更点及与项目方向的关系

README 定位是"人人可用的**易、快、便宜**的全模态模型服务"，本次提交从三个维度直接呼应：

- **"易"（易用/可靠）**：Qwen3-Omni、Qwen3-TTS、MiniCPM-o 4.5 等主流全模态模型的流式文本输入（#9799、#10728）、语音专用管道的请求校验（#9997）、模型 revision 启动预取修复（#11165），降低用户接入与使用门槛；x_to_text 示例清理、TTS 失败音频保留等改善开发体验。
- **"快"（性能）**：扩散侧 Ulysses 序列并行的零拷贝 Q/K/V 交换与 copy-engine 重叠（#11009/#11010）、MiniMax-H3 去噪行更新消除逐步 mask 同步（#10859）、Qwen3-TTS Talker Triton 内核跨 batch 大小一次性编译（#10995）、Ming-TTS 批量化流式合成且声学反馈保留在 GPU（#11113）、Higgs v2 延迟模式 logits 掩码融合（#11119）。
- **"便宜"（硬件覆盖与成本）**：ROCm MI300 覆盖 Qwen3-Omni 实时/Omni/TTS 功能缺口（#11170），NVIDIA SM120 VAE 解码器融合算子（#11067），XPU/MiniCPM-o 4.5 部署修复（#11112），NPU CI 去除内部镜像（#9516）——多后端（AMD/Intel/NVIDIA/NPU）并行推进，扩大可负担硬件生态。

## 3. 对项目的影响和潜在意义

- **测试体系成熟化**：ROCm NIGHTLY 大幅扩张（四卡 PP2/CFG2、FLUX/MOSS-Image 分布式数值、28 例 Qwen3-Omni 扩展、Qwen3-TTS 延迟单独资格化、AITER smoke 门控），说明项目正从"功能能跑"转向"跨硬件持续量化达标"，对一个以服务落地为目标的框架是关键里程碑。
- **多模态实时链路补全**：Qwen3-Omni 实时功能、CosyVoice3 TensorRT CFG 批量化、MiniCPM-o 4.5 流式输入与 Thinker-only 管道（#10314）、`/v1/audio/speech/stream` 引入 ping/pong（#10478）——流式/实时全模态服务的协议与模型覆盖面显著增强。
- **稳定性提升**：MoE LoRA 与 NVFP4 ModelOpt 交互（#10264）、LoRA 引擎侧合并第二阶段（#10998）、VAE 统一解码图下禁用旧批量化解码（#9971）等，减少生产环境踩坑概率。

## 4. 值得关注的技术点

- **AI 辅助开发痕迹明显**：多笔提交 Co-authored-by Claude/Claude Opus 5.5/Cursor，且集中在高性能内核与 CI 编排类改动，体现 AI 在底层优化中的深度参与。
- **零拷贝与通信-计算重叠**成为扩散性能优化主线，暗示序列并行规模在增长。
- **编译缓存策略**（Triton 内核一次性编译）与 **MIOpen 搜索资源绑定**（#11110）反映对冷启动延迟和 CI 资源成本的双重关注。
- **NIGHTLY 门控而非硬性 PR 阻塞**的渐进策略，平衡了覆盖扩展与流水线稳定性。

## 5. 对项目发展的综合影响

这批提交显示 vllm-omni 正处在一个以**多后端硬件资格化（ROCm 为重点）+ 流式全模态服务补全 + 底层算子性能深挖**三线并进的阶段：功能层面从"支持模型"走向"支持实时交互式服务"，质量层面从"单点测试"走向"NIGHTLY 全景量化"，性能层面从"算子级优化"走向"通信-计算协同优化"。这些变化直接强化了 README 承诺的"易、快、便宜"，为把全模态推理服务推向更广泛的硬件与生产场景奠定基础；但 CI 体量快速膨胀也埋下维护成本上升的隐患，后续 NIGHTLY 门控策略的收敛值得关注。

## 详细提交记录

### [6ffc07f](https://github.com/vllm-project/vllm-omni/commit/6ffc07f0d4765649b12ac69cc83b49f2648a20ac)

- **作者**: lm10-arg
- **时间**: 2026-11-25T22:34:57Z
- **提交信息**: [CI/Build][ROCm] Add MI300 coverage for Qwen3-Omni realtime, Omni and TTS function gaps (#11170)

Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [722a710](https://github.com/vllm-project/vllm-omni/commit/722a710f79a8abea644cfe4f970a24c906b58e2b)

- **作者**: trueoneplusone
- **时间**: 2026-11-25T22:18:46Z
- **提交信息**: [Model] Support batched CosyVoice3 TensorRT CFG execution (#7794)

Signed-off-by: trueoneplusone <78432179+trueoneplusone@users.noreply.github.com>

### [670204d](https://github.com/vllm-project/vllm-omni/commit/670204dae9c166eb2e3775304288223fe0d6bddd)

- **作者**: biuxs
- **时间**: 2026-11-25T21:45:37Z
- **提交信息**: [Bugfix] Honor model revision during startup prefetch and pipeline discovery (#11165)

Signed-off-by: biuxs <595711149@qq.com>

### [9af9ebc](https://github.com/vllm-project/vllm-omni/commit/9af9ebc14be0570bc42b98125e5846857b6c00f6)

- **作者**: Nyamkhuu Demberelsuren
- **时间**: 2026-11-25T21:02:32Z
- **提交信息**: [Model] Batch Ming-TTS dense 0.5B streaming synthesis and keep acoustic feedback on GPU (#11113)

Signed-off-by: Nyamkhuu Demberelsuren <14359292+d-nyamkhuu@users.noreply.github.com>
Co-authored-by: Nyamkhuu Demberelsuren <14359292+d-nyamkhuu@users.noreply.github.com>

### [801bef7](https://github.com/vllm-project/vllm-omni/commit/801bef70ede78bfa46f9d6a70b51f4bdafdde950)

- **作者**: He Yingxu
- **时间**: 2026-11-25T20:06:59Z
- **提交信息**: [Perf][Qwen3-TTS] Compile the Talker's Triton kernels once for every batch size (#10995)

Signed-off-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [de38f76](https://github.com/vllm-project/vllm-omni/commit/de38f76ec9b6ecb9b3c730c47dd9d13e2ca3fb81)

- **作者**: YU XINYUAN
- **时间**: 2026-11-25T19:27:37Z
- **提交信息**: [Feat][Qwen3-TTS] Support native streaming text input for Qwen3-TTS CustomVoice models (#9799)

Signed-off-by: YU Xinyuan <yuxinyuan02@corp.netease.com>
Co-authored-by: YU Xinyuan <yuxinyuan02@corp.netease.com>

### [4b2c0d7](https://github.com/vllm-project/vllm-omni/commit/4b2c0d731968b04319ec17f39868f501bc343511)

- **作者**: Andrés Marafioti
- **时间**: 2026-11-25T18:49:37Z
- **提交信息**: [Bugfix] Load Qwen3-TTS codec encoder weights in precompute_custom_voice (#11166)

Signed-off-by: Andres Marafioti <andimarafioti@gmail.com>

### [c172cc2](https://github.com/vllm-project/vllm-omni/commit/c172cc284b580cad4589c45346ec8313f54908e8)

- **作者**: ziruil
- **时间**: 2026-11-25T18:22:14Z
- **提交信息**: [Test][Qwen2.5-Omni] Drive Qwen2Model.forward in the Talker projection test (#11140)

Signed-off-by: ziruil <ziruil@nvidia.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [21f4202](https://github.com/vllm-project/vllm-omni/commit/21f420241e39a9497daef941172bc989a2d6d035)

- **作者**: Chendi.Xue
- **时间**: 2026-11-25T17:55:35Z
- **提交信息**: [Bugfix][XPU] MiniCPM-o 4.5: run the default deploy on Model Runner V2 and fix the Code2Wav dependency docs (#11112)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [ab08f64](https://github.com/vllm-project/vllm-omni/commit/ab08f64cf7a647e6d389930adbe0083113d890a6)

- **作者**: noone-zhhh
- **时间**: 2026-11-25T17:25:21Z
- **提交信息**: [Bugfix] Reject unsupported generation requests for speech-only TTS pipelines (#9997)

Signed-off-by: noone-zhhh <workallday.zhh@gmail.com>

### [f8030ad](https://github.com/vllm-project/vllm-omni/commit/f8030ad9ca8db1809349c77f6b65701b56f71819)

- **作者**: SYLAR
- **时间**: 2026-11-25T13:14:43Z
- **提交信息**: [Hardware][NVIDIA][MiniMax-H3] Enable VAE decoder fused ops on SM120 (#11067)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [979f6c7](https://github.com/vllm-project/vllm-omni/commit/979f6c7dfece897f4525289085e67770a56e705e)

- **作者**: SYLAR
- **时间**: 2026-11-25T13:11:16Z
- **提交信息**: [Perf][Diffusion] Overlap the copy-engine Ulysses exchange with head-chunked attention (#11010)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e6ce065](https://github.com/vllm-project/vllm-omni/commit/e6ce06567994e4acf6ef7027c60f41801d02ccc9)

- **作者**: SYLAR
- **时间**: 2026-11-25T13:09:56Z
- **提交信息**: [Perf][Diffusion] Ulysses a2a_permute: zero-copy Q/K/V exchange (#11009)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9900844](https://github.com/vllm-project/vllm-omni/commit/99008443b48c2458fb1776977b24b8dfd3f532ed)

- **作者**: amy-why-3459
- **时间**: 2026-11-25T12:35:56Z
- **提交信息**: [Bugfix] Preserve JoyAI ASR instructions across camera observations (#11012)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [1e1cde7](https://github.com/vllm-project/vllm-omni/commit/1e1cde7fb9e9dd2bbba6090f76d1eb38453a9a86)

- **作者**: SYLAR
- **时间**: 2026-11-25T12:26:40Z
- **提交信息**: [Perf][Diffusion] MiniMax-H3: index-based denoise row updates without per-step mask and unique syncs (#10859)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a357c19](https://github.com/vllm-project/vllm-omni/commit/a357c1999547ca077f18af46b21cbb33aa706698)

- **作者**: psv666
- **时间**: 2026-11-25T12:23:43Z
- **提交信息**: [CI/Build] Clean up Qwen3-Omni benchmark and test names (#10986)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [1626655](https://github.com/vllm-project/vllm-omni/commit/1626655990943d70cb4a3cce500a55790b84777f)

- **作者**: EddieTzy
- **时间**: 2026-11-25T11:38:20Z
- **提交信息**: [Model] Fuse Higgs v2 audio delay-pattern logits masking (#11119)

Signed-off-by: 陶子粤 <1137898187@qq.com>

### [fa740d2](https://github.com/vllm-project/vllm-omni/commit/fa740d2f5a7e7a83ede509f4ef36f7180a2a695f)

- **作者**: chenqi49
- **时间**: 2026-11-25T10:42:20Z
- **提交信息**: ci: remove internal cache-service mirror from NPU CI files (#9516)

Signed-off-by: chenqi49 <479148871@qq.com>

### [43bb649](https://github.com/vllm-project/vllm-omni/commit/43bb649b6b1f51e10118d15d9cdfe21375efe095)

- **作者**: Dong1017
- **时间**: 2026-11-25T08:40:33Z
- **提交信息**: [Bugfix] Simplify diffusion IPC D2H staging (#10790)

Signed-off-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [48ccd75](https://github.com/vllm-project/vllm-omni/commit/48ccd7566e56cfd2393826d7d6c54de372252f3b)

- **作者**: Dominik Farhan
- **时间**: 2026-11-25T08:06:12Z
- **提交信息**: [Bugfix] Skip implicit MoE LoRA for native ModelOpt NVFP4 (#10264)

Signed-off-by: Dominik Farhan <dfarhan@nvidia.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [95513b5](https://github.com/vllm-project/vllm-omni/commit/95513b5322fc78fe3b47bd02b9244d30ba6f0e20)

- **作者**: Arunkumar Eli
- **时间**: 2026-11-25T05:09:56Z
- **提交信息**: [Core][LoRA] Engine-side LoRA merge phase 2: hardening, capability interface, and endpoint fusion (#10998)

Signed-off-by: Arunkumar Eli <elrarun@gmail.com>

### [21a1d1b](https://github.com/vllm-project/vllm-omni/commit/21a1d1bcc99de83cc23dadbb323dbe82133097df)

- **作者**: Yucheng Hu
- **时间**: 2026-11-25T04:41:25Z
- **提交信息**: [CI/Build] Retain failing TTS audio in weekly TTS steps (#9786)

Signed-off-by: Yucheng Hu <89879759+ychu824@users.noreply.github.com>
Signed-off-by: Yucheng Hu <yc6820@outlook.com>

### [aea150e](https://github.com/vllm-project/vllm-omni/commit/aea150e7f00c47b9de2bccb43b5cce87cc3db5ad)

- **作者**: KaiMao LEE
- **时间**: 2026-11-25T04:10:27Z
- **提交信息**: [Bugfix] Remove unsupported global mode from x_to_text example (#10522)

Signed-off-by: 开茂 <likaimao.lkm@alibaba-inc.com>
Co-authored-by: 开茂 <likaimao.lkm@alibaba-inc.com>

### [3a77798](https://github.com/vllm-project/vllm-omni/commit/3a7779866bd5f9d55114ec06110c170464582dc9)

- **作者**: Howard Yang
- **时间**: 2026-11-25T04:06:04Z
- **提交信息**: [Model] Register a Thinker-only pipeline profile for MiniCPM-o 4.5 (#10314)

Signed-off-by: HowardYangAI <13777842855@163.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [aaa4386](https://github.com/vllm-project/vllm-omni/commit/aaa43866dbe30ed49e9fc87d21becdad54c0e61a)

- **作者**: hac17
- **时间**: 2026-11-25T03:47:47Z
- **提交信息**: [Bugfix][ROCm] Warm Qwen3-TTS eager decoder shapes before readiness (#11111)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [a57d6d1](https://github.com/vllm-project/vllm-omni/commit/a57d6d1a73c694476ae1cc1447bcd765dfd47dd7)

- **作者**: Clodagh Walsh
- **时间**: 2026-11-25T03:17:38Z
- **提交信息**: Introduce ping/pong to /v1/audio/speech/stream (#10478)

Signed-off-by: Clodagh Walsh <clodaghwalsh17@gmail.com>

### [649e7b3](https://github.com/vllm-project/vllm-omni/commit/649e7b3b9a5b93f9a33f753942df149ba939e523)

- **作者**: Ryn Wang
- **时间**: 2026-11-25T02:30:21Z
- **提交信息**: [Bugfix] Disable the legacy batched VAE decode when the unified decode graph runs (#9971)

Signed-off-by: Ryn Wang <Ryn.Wang@outlook.com>

### [71f3ce0](https://github.com/vllm-project/vllm-omni/commit/71f3ce024771df2a50389ef35915333765e24100)

- **作者**: amy-why-3459
- **时间**: 2026-11-25T01:59:34Z
- **提交信息**: [CI/Build] Require complete Seed-TTS request coverage (#10544)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [574fb73](https://github.com/vllm-project/vllm-omni/commit/574fb730d1e8b11eab302fba2c293ccbfc1d022c)

- **作者**: haic0
- **时间**: 2026-11-25T01:54:55Z
- **提交信息**: [CI/Build][ROCm] Gate MiniCPM-o DuplexEval completion in NIGHTLY (#11103)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [4ea01c4](https://github.com/vllm-project/vllm-omni/commit/4ea01c4dd1531bf6149f057efe75a2b2f1ed55e5)

- **作者**: haic0
- **时间**: 2026-11-25T01:50:28Z
- **提交信息**: [CI/Build][ROCm] Qualify Qwen3-TTS latency separately in NIGHTLY (#11106)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [ac0503f](https://github.com/vllm-project/vllm-omni/commit/ac0503f6b312d887eb829e6f6ef3b874841d641d)

- **作者**: haic0
- **时间**: 2026-11-25T01:46:29Z
- **提交信息**: [CI/Build][ROCm] Add offline image-to-video README coverage to NIGHTLY (#11096)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [df98ea7](https://github.com/vllm-project/vllm-omni/commit/df98ea7898db7e4e0676a1a1f7acc039a283e939)

- **作者**: Joshna-Medisetty
- **时间**: 2026-11-25T01:28:13Z
- **提交信息**: Fix ming3 tts xpu flash attn (#10277)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [3d017ee](https://github.com/vllm-project/vllm-omni/commit/3d017ee88cced87a60c647659ac65d1d45430e84)

- **作者**: amy-why-3459
- **时间**: 2026-11-25T00:58:58Z
- **提交信息**: [Model] Support MiniCPM-o 4.5 streaming text input (#10728)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4f0ea12](https://github.com/vllm-project/vllm-omni/commit/4f0ea122d815963ad07284ddecda82d4af8a44e2)

- **作者**: haic0
- **时间**: 2026-11-25T00:46:55Z
- **提交信息**: [CI/Build][ROCm] Qualify the 28-case Qwen3-Omni NIGHTLY expansion (#11105)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>

### [4f27166](https://github.com/vllm-project/vllm-omni/commit/4f27166451401dc69f334be2d5d2c2016c7317d6)

- **作者**: haic0
- **时间**: 2026-11-25T00:46:07Z
- **提交信息**: [CI/Build][ROCm] Add four-GPU PP2 and CFG2 parity to NIGHTLY (#11098)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>

### [bd31bda](https://github.com/vllm-project/vllm-omni/commit/bd31bda989867b27308a587a0ab164b7e386e402)

- **作者**: haic0
- **时间**: 2026-11-25T00:45:19Z
- **提交信息**: [CI/Build][ROCm] Add FLUX and MOSS-Image distributed numerics to NIGHTLY (#11097)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>

### [b6e01fc](https://github.com/vllm-project/vllm-omni/commit/b6e01fc842617d43ec5325f8f2d4aa673db4af10)

- **作者**: htydecode
- **时间**: 2026-11-25T00:36:59Z
- **提交信息**: [Model] Qwen3-TTS: compute reference encoder padding with integers (#10096)

Signed-off-by: htydecode <81070259+htydecode@users.noreply.github.com>
Signed-off-by: htydecode <409919778@qq.com>

### [01d6a8e](https://github.com/vllm-project/vllm-omni/commit/01d6a8edae67a78186444dc0fbde66edb8d0c6cf)

- **作者**: hac17
- **时间**: 2026-11-25T00:11:26Z
- **提交信息**: [CI/Build][ROCm] Bound Qwen perf host pools and MIOpen search (#11110)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [5cf7f5d](https://github.com/vllm-project/vllm-omni/commit/5cf7f5d369bb2916e3d3473e105fcf4a8a479161)

- **作者**: haic0
- **时间**: 2026-11-25T00:10:50Z
- **提交信息**: [CI/Build][ROCm] Gate the Qwen3-Omni AITER smoke in NIGHTLY (#11102)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>

---
