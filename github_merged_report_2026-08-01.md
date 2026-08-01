# GitHub Stars 合并报告 - 2026-08-01

**合并日期**: 2026-08-02
**监控日期**: 2026-08-01
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


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2117
- **最后更新**: 2026-08-01T00:58:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2552
- **最后更新**: 2026-08-01T06:19:12Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
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


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6080
- **最后更新**: 2026-08-01T16:31:15Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3901
- **最后更新**: 2026-07-31T15:51:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34213
- **最后更新**: 2026-08-01T21:24:43Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Henos D

## AI分析总结

### 1. 主要更新类型
**文档更新**。本提交仅修改 scheduler 相关的 docstring，无任何代码行为变更。

### 2. 关键变更点及其与项目整体方向的关系
- 为 16 个 scheduler 方法补充了签名中存在但 `Args:` 块遗漏的参数说明，例如：
  - DPMSolver 单步/多步及 cosine 多步更新方法中的 `noise` 参数（sde-* 算法类型必需）；
  - DPMSolver `set_timesteps` 中的 `mu` 参数；
  - CogVideoXDDIM 和 DDIMInverse 的 `device` 参数；
  - Helios UniPC 方法中的 `sigma`/`sigma_next`/`sigma_before`。
- 修正了 `scheduling_dpm_cogvideox` 中 `rescale_zero_terminal_snr` 的文档错误：原文档提到了不存在的 `betas` 参数，实际应为 `alphas_cumprod`。
- 通过 `make fix-copies` 将 `scheduling_dpmsolver_multistep_inverse` 的变更自动同步到其他副本文件，保持代码库一致性。

这些变更直接服务于 diffusers 作为**易用的扩散模型工具库**这一目标：scheduler 是扩散管线的核心组件，精确完整的 API 文档能帮助用户正确选择算法参数，尤其是 sde-* 等高级算法所需的参数，降低使用门槛。

### 3. 对项目的影响和潜在意义
- **提升文档质量与可信度**：补全缺失的参数说明，修复错误参数名，减少用户因文档误导而产生的错误配置。
- **降低维护成本**：通过 `fix-copies` 保持派生文件同步，体现了项目对代码一致性的严格管理，为后续扩展新 scheduler 提供了模板。
- **无运行时风险**：纯文档修改适合作为低风险提交合并，对现有功能零影响，但显著改善开发者体验。

### 4. 值得关注的技术点
- **文档与签名一致性检查**：提交针对的是参数遗漏，暗示项目可能缺少自动校验 docstring 与函数签名的 CI 工具，未来可考虑引入 `docstring_parser` 或 `pydocstyle` 类工具来强制保证。
- **多文件同步机制**：`make fix-copies` 是 diffusers 用于管理相似代码模块（如不同 scheduler 版本）的工程实践，值得学习，可避免手工同步带来的遗漏。

### 5. 基于项目背景，这些提交如何影响项目发展
diffusers 作为 HuggingFace 生态中扩散模型的核心库，其 API 文档的完善直接影响用户采纳率。本次提交虽然零功能改变，但**增强了库的可用性和专业度**，有助于吸引更广泛的开发者（尤其是研究者和初学者）使用 scheduler 自定义采样流程。持续进行的文档治理也体现了项目向“生产级、高可维护性”演进的趋势，为后续引入更多 scheduler 类型（如更高效的采样器）打下坚实基础。

## 详细提交记录

### [4b8e466](https://github.com/huggingface/diffusers/commit/4b8e466bfda053b25ac3e13444fcd5e7e706f3cb)

- **作者**: Henos D
- **时间**: 2026-08-01T21:24:19Z
- **提交信息**: Add missing `Args:` entries to scheduler docstrings (#14354)

Add missing Args entries to scheduler docstrings

Sixteen scheduler methods had Args: blocks that omitted parameters present
in the signature. Adds the missing entries:

- noise, on the DPMSolver single/multistep and cosine-multistep update
  methods (required by the sde-* algorithm types)
- mu, on DPMSolverMultistep/Singlestep set_timesteps
- device, on CogVideoXDDIM and DDIMInverse set_timesteps
- sigma / sigma_next / sigma_before, on the Helios UniPC methods

Also corrects the rescale_zero_terminal_snr entry in scheduling_dpm_cogvideox,
which documented a `betas` parameter the function does not take (it takes
alphas_cumprod).

The scheduling_dpmsolver_multistep_inverse change is propagated by
make fix-copies, not hand-edited.

Documentation only; no behavior change.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
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


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
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


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31056
- **最后更新**: 2026-08-01T21:57:28Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 8
- **主要提交者**: Zhangheng, Jackey Hua, JemmaFan

## AI分析总结

### 主要更新类型
- **功能新增**：支持 Kimi K3 的推理、工具调用及 OpenAI 兼容服务；AMD AITER 根据输入形状推导校验参数。
- **Bug 修复**：修复 GLM5.2 上下文并行（CP v2）问题；修复 Rust 服务器 TCP 层首字延迟（TTFT）卡顿；修复 chunked-prefix-cache 门控配置未生效的问题。
- **性能优化**：为 NemotronH 禁用可断开的 CUDA graph；限制 flashinfer_deepgemm FP8 GEMM 的 M 范围以保持性能稳定。
- **文档更新**：重写 runtime-context 技能文档；新增 H200/B200 DeepSeek-V4 Flash 官方验证结果。
- **重构与测试**：核心为配置系统向命名空间模型迁移（role-based namespace）的系列重构；恢复此前跳过的配置迁移测试；新增 PR 测试。

### 关键变更点与项目方向
1. **配置架构现代化**：多个提交（6-10）将 `ServerArgs` 的集中式配置拆解为按角色/命名空间（exec/memory/schedule/parallel 等）隔离的“bag”访问器，并逐步淘汰 `ServerArgs.override`。这是对多进程、多角色部署场景的基础设施升级，使配置更可追踪、可审计，与 SGLang 作为高可扩展推理框架的目标一致。
2. **新模型/硬件支持**：Kimi K3、GLM5.2、NemotronH、DeepSeek-V4 Flash 验证以及 AMD 优化，持续扩大框架的模型和硬件兼容性，符合“高效服务先进模型”的定位。
3. **稳定性与性能**：Rust 服务器 TCP 层修复直接降低 TTFT，量化约束与 CUDA graph 调整均为端侧延迟/吞吐调优，贴合低延迟推理目标。

### 影响和潜在意义
- **架构优化**：配置命名空间迁移使系统更符合“职责分离”原则，为未来动态配置、热更新和更复杂的多节点调度奠定基础，但也引入了一部分 internal API 

## 详细提交记录

### [e2cf21b](https://github.com/sgl-project/sglang/commit/e2cf21b9e5615e1b485dcbb8f4cd6a56889010ae)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-01T21:57:23Z
- **提交信息**: [Kimi K3] Add reasoning, tool-call, and OpenAI serving support (#33025)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>
Co-authored-by: A-transformer <cl5743590921@gmail.com>

### [f1b41a5](https://github.com/sgl-project/sglang/commit/f1b41a5b3df70639677f98038e70e74864dd81ab)

- **作者**: Zhangheng
- **时间**: 2026-08-01T20:50:10Z
- **提交信息**: [CP]: FIx some issue for glm5.2 cp v2 (#33100)

### [e0ba311](https://github.com/sgl-project/sglang/commit/e0ba311026f9840b98f1a6bfa856be9d2ae010d7)

- **作者**: Brayden Zhong
- **时间**: 2026-08-01T20:48:58Z
- **提交信息**: Disable breakable CUDA graph for NemotronH (#33130)

### [574ead7](https://github.com/sgl-project/sglang/commit/574ead753a88ace24fb5870ff0f60e3db4ce09cb)

- **作者**: Kan Wu
- **时间**: 2026-08-01T19:13:13Z
- **提交信息**: [rust-server] fix TCP-layer TTFT stalls (#33026)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>

### [00a219f](https://github.com/sgl-project/sglang/commit/00a219f6c9e5b38ec7beddcfcb99266601182443)

- **作者**: Jackey Hua
- **时间**: 2026-08-01T16:36:13Z
- **提交信息**: [Quant] Keep the flashinfer_deepgemm FP8 GEMM to 1 <= M < 32 (#32843)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [729081e](https://github.com/sgl-project/sglang/commit/729081e14f6aa94abec491738241c3a1542bd66f)

- **作者**: Cheng Wan
- **时间**: 2026-08-01T16:00:10Z
- **提交信息**: docs: rewrite the runtime-context skill for the namespace-bag config model (#33173)

The skill still described the retired resolve-at-end contract (a single
resolved ServerArgs as the source of truth, ServerArgs.override as the
mutation entry). Rewrite the config sections for the landed model:

- ServerArgs is a pristine published seed; resolved config lives in the
  namespace bags (get_exec()/get_memory()/.../get_device()), projected at
  publish(server_args, role=...) per process entry.
- Post-publish mutation goes through get_context().override (bag-only);
  ServerArgs.override is being retired behind the writer ratchet, and
  rerouting a writer co-flips all its readers in the same commit.
- Documented the reads that stay on an instance (per-runner fork fields,
  per-instance tokenizer/entrypoints boundaries, whole-object passes),
  get_parallel()'s config/live dual semantics with the live-shadowed
  sizes rule, preserve_config for nested publishes, and the bag-only
  declare_load_time_override route.
- Testing idioms: publish-seeding (override_server_args + scoped bag
  overrides) instead of faking accessors or SimpleNamespace stand-ins;
  per-file test runs to avoid leaked-publish masking.
- Guardrails: added the writer ratchet, namespace-coverage lint, and the
  migration-deferral ratchet.

### [7071cfb](https://github.com/sgl-project/sglang/commit/7071cfb873a403bba48bf1d700129eec358735cf)

- **作者**: Cheng Wan
- **时间**: 2026-08-01T15:59:49Z
- **提交信息**: runtime_context: per-role namespace enforcement behind SGLANG_ROLE_NAMESPACES (#33172)

publish(role=...) has recorded provenance since the namespace split; this
wires the enforcement the role was reserved for. SGLANG_ROLE_NAMESPACES
selects the mode:

- off (default): no bookkeeping; the mode gate in config_bag stays a
  dead-branch-prunable check under dynamo (bag reads run inside compiled
  forwards — pinned by a fullgraph test).
- record: audit mode — collect (role, namespace) pairs per process and
  persist each new pair immediately to SGLANG_ROLE_NAMESPACES_OUT (worker
  teardown skips atexit), plus a per-process stderr summary at exit.
- enforce: a bag read outside the role's ROLE_NAMESPACE_SETS entry fails
  closed with an actionable error; None entries mean full tree.

Sets are filled only where audits back them: dp_controller reads only
exec (record-mode plain + DP-attention smokes agree with the module's
static read set — the elastic-EP gate). tokenizer observed zero bag
reads (per-instance managers read self.server_args by design) but keeps
the full tree until the multi-tokenizer disagg shape (TokenizerWorker's
get_disagg read) is audited; encoder / expert_backup /
weight_cache_daemon likewise await their deployment shapes.

Verified end-to-end: DP-attention smoke under enforce boots and serves
with zero violations.

### [9b44695](https://github.com/sgl-project/sglang/commit/9b4469571336140f19bbb6436a408e1e10069bd8)

- **作者**: Cheng Wan
- **时间**: 2026-08-01T15:59:27Z
- **提交信息**: test: recover the config-namespace-migration deferrals (#33171)

The module-skipped tests injected config by faking get_server_args (a
SimpleNamespace stand-in patched onto the module) or by writing fields
onto a ServerArgs instance post-publish — both invisible to the namespace
accessors the production code now reads. Re-enable them by publishing the
config they need (get_context().override_server_args seeding, scoped per
test), asserting bag state where the old assertions checked instance
write-through (declare_load_time_override is bag-only), and extending the
per-runner stubs the code genuinely reads (kv_cache_dtype_str,
max_total_tokens, context_len).

The unified-radix-cache file (which grew a large hicache/insert-walk suite
while skipped) is recovered in the same change:

- test_cache_finished_req_strips_thinking (19 parametrized classes) wrote
  strip_thinking_cache onto the ServerArgs instance; the cache reads
  get_serving().strip_thinking_cache — use the serving bag's scoped
  override.
- test_shallower_crossing_backs_up_above_backuped_middle staged its
  broken-backup-continuity setup through insert_host, which now
  deliberately drops refills below an un-backed-up node under
  write-through (host_insert_dropped). Build the same tree state through
  an explicit backup + device eviction.

Every config-namespace-migration deferral is recovered, so the deferral
ratchet (test_migration_deferral_ratchet.py) has done its job and is
retired.

### [47d8b5b](https://github.com/sgl-project/sglang/commit/47d8b5b749fd91d6f9bd3ed3c1726798610ae5d9)

- **作者**: Cheng Wan
- **时间**: 2026-08-01T15:58:39Z
- **提交信息**: config: route parallel config-leaf reads through get_parallel() (#33170)

The parallel namespace joins the accessor migration: 106 config-leaf reads
(enable_dp_lm_head, enable_dp_attention, pp_async_batch_depth, dp_size,
ep_join_rank_offset, dwdp_size, ...) flip from get_server_args()/
self.server_args to get_parallel(), which serves config leaves from the
published parallel bag via __getattr__.

- ParallelContext.__getattr__ is restructured to stay dynamo-traceable
  (object.__getattribute__ graph-breaks): gate helpers such as
  enable_moe_dense_fully_dp() run inside compiled model forwards. A
  fullgraph regression test pins the pattern.
- The five live-shadowed topology sizes (tp/pp/dcp/attn_cp/moe_dp_size)
  keep their server_args reads: the live @property wins on the accessor,
  and conditionally-initialized groups would fail loud at unconditional
  call sites.
- Elastic-EP scale writers (ep_size/dp_size x4 in model_runner) reroute
  to get_context().override together with their remaining instance
  readers (expert_location gpus-per-node paths); the ServerArgs.override
  ratchet drops 39 -> 35.
- The expert placement helpers (compute_logical_to_rank_dispatch_
  physical_map, _compute_logical_to_all_physical_map,
  _prefer_same_node_experts) now read everything from the bags and drop
  their server_args parameter; their unit tests publish the config they
  need instead of stubbing it.

### [df55e91](https://github.com/sgl-project/sglang/commit/df55e911d6212e7ebdd66cb6738b88fdd1040ef2)

- **作者**: Cheng Wan
- **时间**: 2026-08-01T15:57:28Z
- **提交信息**: Fix the chunked-prefix-cache gate writing config the backends never read (#33168)

The load-time gate (maybe_disable_chunked_prefix_cache) wrote its
ServerArgs instance while every reader has moved to the published
config: the attention backends assert / branch on
get_schedule().disable_chunked_prefix_cache when they initialize, so the
flip never reached them and a backend outside
CHUNKED_PREFIX_CACHE_SUPPORTED_ATTENTION_BACKENDS kept chunked prefix
enabled.

Reroute the writer through get_context().override (which writes the
published bags) and flip the two remaining instance reads — the gate's
own log check and the prefill cuda-graph runner's capture flag — to the
bag. A regression test pins the three contracts: the gate lands on the
bag, the pristine ServerArgs instance stays untouched, and the
draft-worker guard never writes.

The ServerArgs.override call-site ratchet drops 39 -> 38.

### [ae84811](https://github.com/sgl-project/sglang/commit/ae848116662ece923501131ce773a4602223237e)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-01T08:05:42Z
- **提交信息**: [Docs] Add verified H200 and B200 DeepSeek-V4 Flash Official results (#33109)

### [2fd78ec](https://github.com/sgl-project/sglang/commit/2fd78ec2d75149288832080321e061eb9ad445e1)

- **作者**: JemmaFan
- **时间**: 2026-08-01T07:29:25Z
- **提交信息**: [AMD] Derive AITER verify tokens-per-req from input shape (#31221)

### [33ecf4b](https://github.com/sgl-project/sglang/commit/33ecf4bcd82364f3e19f457963d053db94226c22)

- **作者**: Sugar920
- **时间**: 2026-08-01T07:03:21Z
- **提交信息**: Add pr tests (#31952)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>
Co-authored-by: Cherry_ming <136634645@qq.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1240
- **最后更新**: 2026-07-30T09:22:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 87880
- **最后更新**: 2026-08-01T22:17:11Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 11
- **主要提交者**: xiaolinchen, Jeff (Junze) Ma, Guan-Ming Chiu

## AI分析总结

分析生成失败

## 详细提交记录

### [38a466e](https://github.com/vllm-project/vllm/commit/38a466e7b6e087d67c35e7f924c04c245423c99f)

- **作者**: Woosuk Kwon
- **时间**: 2026-08-01T17:22:33Z
- **提交信息**: [DSV4] Implement Sequence Parallelism (#46789)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [dc818c1](https://github.com/vllm-project/vllm/commit/dc818c198d3ff50a16f38eba567da006478239c8)

- **作者**: yzong-rh
- **时间**: 2026-08-01T16:10:26Z
- **提交信息**: [GPT-OSS] Strict tool call and constrained decoding for Harmony (#45560)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [127a7ce](https://github.com/vllm-project/vllm/commit/127a7cebc9e3b76b7558fe96b4156a55a5905375)

- **作者**: Hongxia Yang
- **时间**: 2026-08-01T16:02:44Z
- **提交信息**: Add @hongxiayang as code owner for AMD-specific model files and ROCm docs (#50608)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>

### [03c782e](https://github.com/vllm-project/vllm/commit/03c782eb91f70ba990432aace77f94be66aaeb2e)

- **作者**: Ning Xie
- **时间**: 2026-08-01T15:37:29Z
- **提交信息**: [model registry] some simple typos (#50673)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [39f55ff](https://github.com/vllm-project/vllm/commit/39f55ffdaacbf4f2ac06e395c3f9c6e55a54dbd0)

- **作者**: Almog Tavor
- **时间**: 2026-08-01T15:10:51Z
- **提交信息**: [Core] Offload raw-prompt preprocessing to renderer thread pool in AsyncLLM (#49608)

Signed-off-by: almogtavor <almogtavor@gmail.com>

### [63e78ce](https://github.com/vllm-project/vllm/commit/63e78ce3652f4f94e9f484f40db71ca4cf019f21)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-08-01T14:10:56Z
- **提交信息**: [Benchmark] Add probe requests to vllm bench serve (#49611)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>

### [ab06486](https://github.com/vllm-project/vllm/commit/ab06486175e833925be065438b067cec488029e8)

- **作者**: xiaolinchen
- **时间**: 2026-08-01T13:56:55Z
- **提交信息**: [Bugfix][Kernel] Fix dangling temporary in AWQ gemm torch::stable::sum dim arg (#46805)

Signed-off-by: wentian-byte <2990624738@qq.com>

### [652ba59](https://github.com/vllm-project/vllm/commit/652ba59229499eb65fc4115b7feadeddf9bcb75d)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-01T11:55:36Z
- **提交信息**: [Model Runner V2] Enable encoder token embedding (#50574)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [3986b96](https://github.com/vllm-project/vllm/commit/3986b967b249468fc1bd052f89a1eeeada6377b4)

- **作者**: Jeff (Junze) Ma
- **时间**: 2026-08-01T09:41:43Z
- **提交信息**: (feat): optionally disable lookup on PD decode (#50498)

Signed-off-by: Jeff Ma <jeffjma@umich.edu>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [81a42d3](https://github.com/vllm-project/vllm/commit/81a42d37b1d76a34ce75b6871bba57a30cddc812)

- **作者**: Cao Qian
- **时间**: 2026-08-01T07:36:42Z
- **提交信息**: [Frontend] Add cache_salt support to Anthropic Messages API (#49498)

Signed-off-by: aeon-x <talexcao@gmail.com>

### [77469c9](https://github.com/vllm-project/vllm/commit/77469c9057bec3212a64877dbbf3b9c48c22d786)

- **作者**: Matt Qin
- **时间**: 2026-08-01T07:17:17Z
- **提交信息**: [ROCm][MLA] Mask the AITER MLA small-head verify flatten causally (#50476)

Signed-off-by: yudigege86 <naqin@amd.com>
Co-authored-by: yudigege86 <naqin@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-02
**监控日期**: 2026-08-01
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5782
- **最后更新**: 2026-08-01T21:19:04Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: Zhou Taichang, SYLAR, Librium

## AI分析总结

### 主要更新类型
- **全部为 Bug 修复**（共 6 项），无新增功能、性能优化或文档更新。

### 关键变更点
- **推理安全与接口兼容**：拒绝 `thinker+talker` 模型在未启用 `--trust-remote-code` 时使用 `/v1/completions`，避免未授权代码执行风险。
- **分布式 KV 缓存一致性**：修复纯张量并行（TP）下 KV 接收回退的跨 rank 一致性，改为全有或全无策略，防止部分 rank 状态不同步。
- **多模态生成参数修正**：修复 Wan2.2 中 `guidance scale` 分辨率丢失的问题，确保视频生成质量稳定。
- **输出/输入格式统一**：将图像文件元数据与目标输出格式对齐，避免格式不匹配导致的处理异常。
- **恢复关键推理路径**：重新启用 BAGEL 中 CFG KV 传输，修复因历史改动丢失的功能。
- **张量布局保持**：确保视频张量保持 channel-last 布局，适配下游算子的内存访问要求。

### 对项目的影响与意义
- 这些修复直接提升了多模态服务（尤其是视频、图像、混合推理模型）的**稳定性和正确性**，减少了分布式环境下因 KV 不一致或张量布局错误引发的静默失败。
- 安全相关修复强化了服务在不可信代码场景下的防御能力，符合生产环境部署的基本要求。
- 针对具体模型（Wan2.2、BAGEL）的修正体现了项目对主流社区模型的快速兼容迭代，有助于吸引更多模型接入。

### 值得关注的技术点
- **TP 下的 KV 全/无接收机制**：设计上避免了部分 rank 成功部分失败导致的推理结果不一致，是分布式推理中常见的隐蔽问题。
- **CFG KV 传输**：涉及 classifier-free guidance 的缓存数据在 prompt 分支间的复用，恢复它意味着优化路径重新生效。
- **channel-last 布局**：对视频模型的性能至关重要，保持布局可免去额外的张量转置开销。
- **`trust-remote-code` 检查**：说明服务端开始区分模型来源，为后续更精细的安全治理打基础。

### 对项目发展的潜在作用
- vllm-omni 的目标是提供“易用、快速、廉价”的全模态服务。这批修复虽小，但覆盖了推理链路中多个

## 详细提交记录

### [67c5477](https://github.com/vllm-project/vllm-omni/commit/67c54777bb22e9e7e08fdf7c47a64f06b566fc47)

- **作者**: ChoHee
- **时间**: 2026-08-01T15:49:12Z
- **提交信息**: [Bugfix] Reject /v1/completions for thinker+talker models when --trust-remote-code is unset (#5525)

Signed-off-by: ChoHee15 <cc5281@126.com>

### [2c4e9a9](https://github.com/vllm-project/vllm-omni/commit/2c4e9a945bdd1ada57df31f131c4f832f3f221d7)

- **作者**: Zhou Taichang
- **时间**: 2026-08-01T15:43:48Z
- **提交信息**: [BugFix] Make pure-TP KV receive fallback all-or-nothing across ranks (#5636)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [4b1547b](https://github.com/vllm-project/vllm-omni/commit/4b1547b4d83cbbbbfc472bed6559240fcf26a594)

- **作者**: SYLAR
- **时间**: 2026-08-01T15:17:33Z
- **提交信息**: [Bugfix] Fix Wan2.2 omitted guidance scale resolution (#5615)

Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>

### [6e8c279](https://github.com/vllm-project/vllm-omni/commit/6e8c279a68c5dda298d418c369d10af2a2a8035c)

- **作者**: SYLAR
- **时间**: 2026-08-01T15:09:27Z
- **提交信息**: [Bugfix] Match image file metadata to output format (#5619)

Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>

### [6f98c80](https://github.com/vllm-project/vllm-omni/commit/6f98c807d29ea9d7ca347bee3bf573a4e69fe028)

- **作者**: SYLAR
- **时间**: 2026-08-01T15:06:05Z
- **提交信息**: [Bugfix] Restore BAGEL CFG KV transfers (#5620)

Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>

### [185e3d6](https://github.com/vllm-project/vllm-omni/commit/185e3d6df60276166349e69fdc1171fd0e50c79f)

- **作者**: Librium
- **时间**: 2026-08-01T07:05:57Z
- **提交信息**: [Bugfix] Preserve channel-last video tensor layout (#5418)

Signed-off-by: pxljs <1621352782@qq.com>

---
