# GitHub Stars 合并报告 - 2026-09-09

**合并日期**: 2026-09-10
**监控日期**: 2026-09-09
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


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2202
- **最后更新**: 2026-09-09T22:49:22Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 3
- **主要提交者**: Bin Jia, Ting, Coach257

## AI分析总结

### 主要更新类型
- **Bug修复**：1项（检查点发布逻辑）
- **重构**：3项（agent工具描述、patchgen技能命名、审查时机调整）
- **文档更新**：伴随重构同步改进
- **功能新增**：1项（数据加载器泛化）

### 关键变更点与项目方向
- **检查点发布修复**：防止多副本训练时，因单副本失败而错误发布不完整检查点，保障分布式训练可靠性。
- **Agent工具链重构**：将工具描述泛化、审查门禁移至PR阶段、移除agent专属工具，使agent能力更通用、可复用，契合“Model-Centric Distributed Recipe Zoo”的模块化理念。
- **Patchgen技能重命名与布局保护**：将“migrate”技能更名为“veomni-patchgen-model”，并拆分指导文档、保护专家布局，使模型迁移流程更清晰、安全。
- **数据加载器泛化**：将MiniMax parquet加载器整合进通用迭代器，减少重复代码，提升多模态数据接入效率。

### 对项目的影响与潜在意义
- 提升分布式训练稳定性，避免脏数据发布。
- 增强agent工具的可移植性和可维护性，降低社区贡献门槛。
- 数据层抽象统一，为后续新模态数据格式接入铺平道路。

### 值得关注的技术点
- 检查点发布的多副本一致性处理。
- Agent工具从“专用”到“通用”的架构演进。
- 数据加载器泛化设计，兼顾兼容性与扩展性。

### 对项目发展的影响
VeOmni旨在提供跨模态训练的分布式配方库。本次提交通过**强化可靠性、简化工具链、统一数据接口**，使项目更接近“开箱即用”的社区友好目标。重构动作表明项目正从“功能堆叠”转向“架构收敛”，为后续大规模扩展和外部贡献奠定基础。数据层与agent层的泛化，也呼应了“Scaling Any Modality”的核心理念。

## 详细提交记录

### [97a6e07](https://github.com/ByteDance-Seed/VeOmni/commit/97a6e07493ef725ea51372b832db02c33dff7cbc)

- **作者**: Ting
- **时间**: 2026-09-09T22:49:16Z
- **提交信息**: [ckpt] fix: do not publish a staged checkpoint when another rank's copy failed (#1172)

### [9234080](https://github.com/ByteDance-Seed/VeOmni/commit/9234080200d303f4a700962abbbf36641a02b503)

- **作者**: Bin Jia
- **时间**: 2026-09-09T13:24:43Z
- **提交信息**: [agent, docs] refactor: describe the agent tooling generically (#1148)

### [6663088](https://github.com/ByteDance-Seed/VeOmni/commit/66630887e257ad83d6a43a008549550ed7c2c10a)

- **作者**: Bin Jia
- **时间**: 2026-09-09T12:59:57Z
- **提交信息**: [agent, docs, model] fix: split patchgen guidance and guard expert layouts (#1147)

### [5b29dc2](https://github.com/ByteDance-Seed/VeOmni/commit/5b29dc24bf21c9c6dfcca36cb3c62ba7846005df)

- **作者**: Bin Jia
- **时间**: 2026-09-09T11:30:50Z
- **提交信息**: [agent, docs] refactor: rename the migrate skill to veomni-patchgen-model (#1145)

### [e1f193f](https://github.com/ByteDance-Seed/VeOmni/commit/e1f193f89e5e0957671512d49324284b0bc56e8f)

- **作者**: Bin Jia
- **时间**: 2026-09-09T08:15:40Z
- **提交信息**: [agent] refactor: move the review gate to PR time and drop agent-specific tooling (#1137)

### [1408fe6](https://github.com/ByteDance-Seed/VeOmni/commit/1408fe654a799fb736e88f4e2f09c4a7dd441b98)

- **作者**: Coach257
- **时间**: 2026-09-09T08:10:26Z
- **提交信息**: [data, model, config, ci] feat: fold MiniMax parquet loader into generic iterable (#1156)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2800
- **最后更新**: 2026-09-09T17:54:01Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), zhangbilang

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交包含**功能新增**（为minimax_h3模型添加持久化AdaLN缓存）和**代码重构**（统一各入口点的请求处理逻辑），无Bug修复或文档更新。

### 2. 关键变更点及与项目方向的关系
- **持久化AdaLN缓存（95e9b86）**：针对minimax_h3视频生成模型，将自适应层归一化（AdaLN）的计算结果缓存并复用，减少推理过程中的重复计算。这与LightX2V“轻量级视频生成推理框架”的核心定位高度一致——通过工程优化降低视频生成的计算开销。
- **统一请求处理（68d0ece）**：将不同入口点（如CLI、API服务、测试脚本等）的请求处理逻辑收敛为统一模式，消除重复代码和分支差异。这服务于框架的**易用性和可维护性**目标，使新增模型或接口时无需为每个入口单独适配。

### 3. 对项目的影响和潜在意义
- **性能层面**：AdaLN缓存直接减少minimax_h3推理时的重复张量运算，对长视频生成场景可显著降低延迟和显存占用，提升吞吐量。
- **架构层面**：请求处理统一化降低了多入口维护成本，为后续扩展新模型、新推理后端（如分布式、量化）提供了更干净的扩展点，减少因入口差异导致的隐性bug。
- **生态层面**：两项改动均属于“内部工程优化”，不改变对外API，但对开发者友好度和推理效率有实质提升，有助于吸引更多模型接入。

### 4. 值得关注的技术点
- **AdaLN缓存策略**：需关注缓存的生命周期管理（何时失效、如何与动态shape兼容）以及缓存命中率对实际加速效果的影响。若实现为“持久化”跨请求缓存，还需考虑多用户并发下的隔离性。
- **请求处理抽象层**：统一逻辑可能引入中间抽象层（如Request/Response标准对象），需观察其是否支持异步、流式输出等视频生成特有需求，以及是否对现有性能敏感路径造成额外开销。

### 5. 对项目发展的影响
LightX2V作为视频生成推理框架，核心竞争点在于**推理速度**和**多模型适配成本**。本次提交从两个维度强化了这一方向：
- **性能护城河**：通过缓存等细粒度优化，使minimax_h3等重模型在消费级硬件上更可用，扩大潜在用户群。
- **架构扩展性**：统一请求处理是框架走向成熟的重要标志——当模型数量增多时，可避免“每个模型一套入口逻辑”的混乱局面，为社区贡献模型提供更低门槛。

整体来看，这两项提交是典型的“内功修炼”，短期不产生新功能，但为框架的长期性能优化和生态扩展奠定基础，符合项目“轻量高效”的定位。

## 详细提交记录

### [95e9b86](https://github.com/ModelTC/LightX2V/commit/95e9b86bff996954420133d5acfd53cd3b7c00cc)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-09T17:53:19Z
- **提交信息**: feat(minimax_h3): add persistent AdaLN cache (#1503)

### [68d0ece](https://github.com/ModelTC/LightX2V/commit/68d0ece544c33558b011844bf6fafa5e2a0c75ed)

- **作者**: zhangbilang
- **时间**: 2026-09-09T12:27:55Z
- **提交信息**: refactor(inference): unify request handling across entrypoints

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2243
- **最后更新**: 2026-09-09T09:40:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6362
- **最后更新**: 2026-09-09T23:02:31Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 13
- **主要提交者**: Jonathan Dierksen, eigen, feih-nv

## AI分析总结

# FlashInfer 提交分析总结

## 一、主要更新类型

本批提交涵盖**Bug修复**（9项）、**功能新增**（3项）、**性能优化**（1项）、**重构**（1项）、**CI改进**（1项）和**基准测试修复**（1项），以修复和稳定性提升为主导。

## 二、关键变更点与项目方向的关系

1. **后端选择逻辑修复**：修复`recurrent_kda`在`backend="auto"`下无法正确回退到CuTe DSL的问题，确保自动后端选择符合文档承诺的语义。该提交揭示了状态约定与内核选择解耦的微妙问题——三个耦合变量需一并恢复，否则多warp路径会写出零行。

2. **JIT缓存失效修复**：将`shutil.copy`改为`shutil.copy2`以保留源文件mtime，避免每次进程启动触发完整重建。报告显示修复前每次进程需216-218秒重建，修复后仅需4.3秒，直接提升生产环境高频启停推理服务的效率。

3. **FP8 KV校准修复**：修复ragged FA2/FA3 prefill中全局k_scale/v_scale被静默忽略的问题，确保FP8 KV缓存量化正确性。

4. **FA2 FP8+GQA解码共享内存越界修复**：修复K+V缓冲区与st.o浮点存储重叠导致的非法共享内存写入崩溃。修复方案需取max(K+V数据, st.o浮点)而非固定假设，体现GQA场景下内存复用的微妙约束。

5. **SM120稀疏MLA挂起修复**：修复spectator IO线程在管线屏障上无限自旋导致的间歇性挂起，根因分析展示了spectator线程与mbarrier同步的经典陷阱。

6. **MiniMax-H3 MXFP8支持**：为NVIDIA B200/B300新增Cake生成的MXFP8 pre-attention实现，紧跟新一代硬件数据格式趋势。

7. **ReplaySSM前缀物化**：新增内核支持在任意token位置物化SSM状态，使前缀缓存与ReplaySSM的环形缓冲机制兼容，补齐该架构在prefix caching场景的能力缺口。

8. **PrimTS API统一重构**：统一实验性PrimTS的`plan()`/`run()`契约，实现静态规划与请求级数据分离，为TensorRT-LLM集成铺路，降低外部LLM框架接入成本。

9. **SM121 FMHA v2 prefill支持**：在DGX Spark（GB10）上验证后启用SM121架构的FlashAttention v2 prefill内核，扩展Blackwell系列GPU覆盖范围。

10. **SM110 GQA解码内核**：新增实验性FP16解码API，针对Thor架构优化，比XQA快5-28%。采用精确JIT加载与SHA-256校验，配合冷L2 CUPTI基准方法，展示严谨的性能验证流程。

11. **MoE量化配置重构**：将混合的QuantVariant拆分为weight/activation/output三个独立格式轴，支持MXFP4×MXFP4等新MMA组合。该设计将"MMA数值格式"与"Python API数据类型"解耦，为后续支持更多量化格式组合奠定架构基础。

12. **DSL_FMHA cubin刷新**：更新预编译内核，在B300上多数形状获得3-8%延迟改善。

13. **基准测试CSV转义修复**：修复含逗号字段导致的数据列偏移问题。

## 三、对项目的影响与潜在意义

这批提交体现了FlashInfer作为高性能推理内核库的成熟化进程，呈现**多硬件架构覆盖**（SM110/121/120）、**量化精度正确性**和**内核性能优化**三条并行主线。JIT缓存修复和挂起修复提升工程稳定性，FP8校准和共享内存越界修复增强可靠性，MXFP8支持和ReplaySSM物化扩展硬件与模型覆盖，PrimTS重构和MoE量化重构强化生态集成与功能边界。整体方向是让项目在保持性能领先的同时，向生产级可靠性和框架友好性持续演进，巩固其在Blackwell/Thor等新一代GPU上作为推理加速基础设施的竞争力。

## 详细提交记录

### [fa2f4d0](https://github.com/flashinfer-ai/flashinfer/commit/fa2f4d0bbfffafee0bf4446697185d7802cd7927)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-09T23:02:08Z
- **提交信息**: fix(kda): make recurrent_kda backend="auto" decode fall back to CuTe DSL (#5037)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes [#4935](https://github.com/flashinfer-ai/flashinfer/issues/4935).
`flashinfer.recurrent_kda(..., backend="auto")` decode raises
`ValueError: the requested Cake recurrent_kda decode contract is
unsupported` on inputs that `backend="cute-dsl"` serves. `"auto"` is the
top-level default, so this is the default path.

`run_recurrent_kda` chooses its state convention before it knows which
kernel will run. The gate commits to Cake's convention on a *candidate*
predicate, and the Cake variant is resolved about 180 lines later. When
the selector returns `None`, the state has already been normalised for a
kernel that will not run, so instead of falling through to CuTe the call
raised.

The docstring already specifies the intended behaviour, and the code
diverged from it: `"cake"` "raises rather than falling back when its
contract is unsupported", while `"auto"` "selects Cake only for its
native equal-head/D128/T1 unbounded-softplus contract **and otherwise
preserves CuTe DSL**". This restores that contract rather than changing
it.

### The fix

Drive the fallback off the **resolved selector result** rather than a
second predicate that has to be kept in step with it. When no variant is
selected under `"auto"`, restore CuTe's state convention before falling
through. `backend="cake"` keeps raising, and the Cake happy path is
untouched.

The subtlety worth reviewing is that the gate writes **three** coupled
variables, so restoring only the obvious one is not enough:

- `state` — Cake passes the pool through; CuTe wants the gathered rows.
- `copy_back_indices` — unset by Cake's arm, required by CuTe's.
- `ssi` — set by Cake's arm and left unset by CuTe's. The one-warp CuTe
route ignores it, but the **multi-warp** route consults it, and a patch
that fixes `state` and `copy_back_indices` while leaving `ssi` set
writes **zero rows** to the state pool. That is a silent wrong answer,
not a crash, which is why the test below exercises both sides of the
`B*HV = 128` threshold.

### Why not tighten the gate instead

Mirroring the selector's preconditions in the gate is the obvious
cheaper fix. It was implemented and measured, and it leaves witnesses
that still diverge — `initial_state_source` with
`initial_state_indices`, a caller `output` aliasing an input, a state
pool large enough to trip the int32-overflow guard, a fused-projection
token row stride, and a padded head dimension. The reason is structural:
`_select_flash_kda_decode_variant` decides on over a hundred predicates
spanning dtypes, strides, alignment, overflow products and aliasing
analysis, and some of what it reads — the output buffer it checks for
aliasing, and the re-wrapped frozen layouts — is not constructed until
after the gate. Most of its arguments *are* available at the gate; the
point is that the aliasing and frozen-layout predicates structurally
cannot be mirrored there, and that mirroring the rest is reimplementing
it, with any drift reintroducing this bug.

Splitting the selector's contract predicates from its layout predicates
is a reasonable follow-up on `main` after the cut, but it is not
required for correctness once the fallback is driven by the resolved
result. The rule worth keeping in review is that **no state convention
may reach the kernel launch before the variant is resolved**.

## 🔍 Related Issues

- Fixes [#4935](https://github.com/flashinfer-ai/flashinfer/issues/4935)
- [#4936](https://github.com/flashinfer-ai/flashinfer/issues/4936) — KDA
API unification audit; this is step 1, and step 2 (documenting `"auto"`
as the top-level default) depends on it

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

All runs on a B200 (CC 10.0).

**The gap was a missing negative contract, not missing coverage.** The
existing
`test_t1_unbounded_softplus_auto_route_tp_shapes_match_cute_with_strided_inputs`
already compares `"auto"` against `"cute-dsl"` on output, state pool and
untouched slots with non-identity indices; every parametrisation it runs
is simply Cake-servable. So this extends that file with the ineligible
cases rather than adding a parallel harness. The new test asserts Cake
is *not* selected, that output and the returned state match
`"cute-dsl"`, that untouched pool slots are bit-identical, and that
`backend="cake"` still raises.

- New test: 3 passed. Reverting only the source hunk makes all three
fail with the exact `ValueError` from the issue.
- `pytest tests/kda/` — **1013 passed, 116 skipped**, no failures
(12m34s), re-run on the current head.
- `pytest tests/kda/test_recurrent_kda_decode_export.py` — 214 passed.
- Direct measurement on the two trigger classes: output and state pool
are **bit-identical** between `"auto"` and `"cute-dsl"` (max diff
`0.0e+00` on both), with the correct non-identity rows mutated, on both
sides of the one-warp threshold.
- Dispatch probe from the issue now reports `auto/l2norm=False -> no
Cake selection` instead of `RAISED Cake-unsupported`, while
`auto/l2norm=True` still selects Cake.

**A third class this PR fixes, found in review and now covered.**
Explicit `T=1` `cu_seqlens` decode is unservable by Cake for *any*
input: the selector requires one accepted-token entry per sequence
(`recurrent_kda.py:1619`) and this path supplies a single scalar
(`:2246`). So `backend="auto"` raised on every such call — including
fully Cake-shaped ones — and the fallback repairs the whole class.
`test_t1_unbounded_softplus_auto_falls_back_to_cute_with_explicit_cu_seqlens`
parametrises `use_qk_l2norm_in_kernel` precisely because eligibility is
irrelevant here; all four cases fail against `upstream/main` with the
issue's `ValueError` and pass on this head, bit-identically to
`"cute-dsl"` on output, returned state and pool.

**The widest class, found while self-reviewing: every GPU that is not CC
10.0 or 10.3.** `auto_unbounded_softplus_candidate` carries no
compute-capability term, but `_select_flash_kda_decode_variant` returns
`None` unless the arch is exactly CC 10.0 or CC 10.3
(`recurrent_kda.py:1484-1488`). So on H100, CC 12.0, CC 12.1 or Rubin
the gate committed to Cake's state convention for the *entire* `T=1`
unbounded-softplus class and then found no variant — a fully Cake-shaped
call raised there just as an ineligible one did. Every test in
`test_recurrent_kda_decode_export.py` requires CC 10.0/10.3 hardware, so
nothing covered it, which is also the substance of CodeRabbit's note on
the `cu_seqlens` test.

`test_t1_unbounded_softplus_auto_falls_back_to_cute_on_unservable_arch`
closes that by emulating the capability rather than switching the
fixture: it patches `get_compute_capability` to CC 9.0 and CC 12.0,
before the `"cute-dsl"` baseline as well so both spellings route
identically and `backend` is the only variable, across both sides of the
one-warp threshold. All four cases fail against `upstream/main` with the
issue's `ValueError`. A CUDA-only fixture would instead assert that the
CuTe DSL decode kernels build on whatever device CI offers, which is a
different claim and one this PR does not establish. **Reviewers with
non-Blackwell hardware:** whether the CuTe DSL decode path runs there at
all is unverified — I only have a B200 — and it decides whether this
class was previously a spurious raise or a different error either way.

**A pre-existing `"cute-dsl"` defect surfaced, deliberately left
alone.** With `ssm_state_indices` containing `-1` (the documented
CUDA-graph padding signal), `"cute-dsl"` gathers `initial_state[-1]` and
copies the result back over the *last* pool slot. Cake correctly skips
inactive rows. Post-fix `"auto"` is bit-identical to `"cute-dsl"` here —
out/state/pool all `0.0e+00` on both sides of the threshold — so this PR
neither introduces nor worsens it, and masking negatives in the fallback
would make `"auto"` accept what `"cute-dsl"` mishandles, breaking the
accepted-set equality this PR establishes. Filed separately as
[#5042](https://github.com/flashinfer-ai/flashinfer/issues/5042), since
it affects `backend="cute-dsl"` directly and the fix needs the one-warp
CuTe route to honor `ssm_state_indices` first — that route currently
ignores them, so the dispatch half alone would write wrong slots on
every one-warp decode.

## Reviewer Notes

**On "restoring the documented contract."** The documentation half holds
— `recurrent_kda.py`, `kda_decode.py`, `kda.py` and
`docs/api/kda_decode.rst` all describe fallback, and none documents
raising. But `git blame` puts the docstring line and the raising gate in
the same commit (#4535), so the documented behaviour never actually
existed in any commit. This brings the code in line with documentation
that was aspirational from birth; it is not a no-op restoration, and
calling it one oversells it.

**Parametrisation asymmetry.** A padded head dimension is only tested
below the one-warp threshold. At the one-warp size `"cute-dsl"` rejects
that layout as well (`Mismatched mQ.strides[2]`), so there is no
divergence to assert and the case would be testing the CuTe launcher,
not this fix.

**Correction — an earlier revision of this note was wrong, and the
second commit fixes what it dismissed.** It claimed the
non-contiguous-`initial_state` residual was benign because the fallback
"mirrors CuTe's own `.contiguous()` handling, so the result is correct."
It does not. `.contiguous()` copies, `copy_back_indices` stayed unset,
and the caller's in-place pool update was dropped **silently** — where
`"cute-dsl"` raises. That is a worse failure mode than the bug this PR
set out to fix, and CodeRabbit was right to flag it. Reviewers should
not have to work around a note that argues against looking.

The second commit closes it, plus a second defect in the same fifteen
lines:

- `initial_state=None` with `ssm_state_indices` set subscripted `None`,
so `"auto"` raised `TypeError` where `"cute-dsl"` succeeds — i.e. #4935
was still open for that input class, merely re-spelled. The gate seeds
zeros there and there is nothing to restore, so the restore is skipped.
- The contiguity guard was skipped for the entire `"auto"` candidate.
Only the *indexed* Cake convention tolerates a strided pool, because it
gathers through `ssi` rather than copying, so the skip is now narrowed
to the indexed case and `"auto"` raises the same guard `"cute-dsl"`
does. This also closes the identical silent drop on the **Cake-served**
path, which predates this PR: before, `"auto"` over a strided pool with
no indices discarded the update whether or not Cake was selected.

Both are covered by
`test_t1_unbounded_softplus_auto_fallback_handles_absent_and_strided_state`,
and each is independently pinned — reverting the `None` guard alone
fails with `TypeError`, reverting the guard narrowing alone fails with
`DID NOT RAISE ValueError`. The invariant the PR now upholds is that
`"auto"`'s accepted input set equals `"cute-dsl"`'s, rather than merely
overlapping it.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved automatic backend selection for recurrent decoding requests
that cannot use the preferred backend, including explicit
sequence-length inputs and unsupported hardware.
* Preserved correct outputs and state updates for indexed,
non-contiguous, or absent initial-state data during fallback processing.
* Added clear errors for unsupported non-contiguous initial-state data
without indices.

* **Documentation**
  * Clarified backend-dependent behavior for returned recurrent state.

* **Tests**
* Added exact-output coverage across fallback, state preservation, and
expected-error scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: kahyunnam <kahyunnam@users.noreply.github.com>

### [826ae81](https://github.com/flashinfer-ai/flashinfer/commit/826ae81b9ec3551698d8ba6f1bf120e5d88c13d7)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-09T22:26:15Z
- **提交信息**: fix(jit): preserve source mtimes when staging rmsnorm_silu and monomoe sources (#5063)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Extends #4798 to the two remaining staging sites named in #4782:
`shutil.copy` → `shutil.copy2` in `jit/rmsnorm_silu.py` and
`jit/monomoe.py`. `shutil.copy` stamps a fresh mtime on staged sources
every process; since JIT freshness is delegated to ninja's mtime scan,
this forced a full rebuild of these modules on every process start.
`copy2` preserves source mtimes so unchanged sources reuse the cached
build.

Verified by running both generators and confirming staged files carry
byte-exact source mtimes.

## 🔍 Related Issues

<!-- Link any related issues here -->

* Issue #4782 
* PR  #4798

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

## Summary by CodeRabbit

- **Performance**
- Reduced unnecessary JIT compilation rebuilds by preserving generated
source file timestamps during copying.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [dbb52c8](https://github.com/flashinfer-ai/flashinfer/commit/dbb52c8a9775840fbfe229eb3b83543a59449b19)

- **作者**: Jonathan Dierksen
- **时间**: 2026-09-09T21:02:42Z
- **提交信息**: ci: log installed Python packages before tests (#5062)

## 📌 Description

Prints the installed Python package list at the end of CI dependency
setup, immediately before the unit-test runner starts.

This records exact versions—including `nvidia-cudnn-frontend` and the
installed cuDNN backend distribution—directly in job logs for future
failure diagnosis.

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
- [x] All tests are passing (`unittest`, etc.).

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

Validated with targeted pre-commit hooks, `bash -n`, ShellCheck, and
`git diff --check`. No GPU or end-to-end CI run was performed; this
change only adds package-version logging before the test runner starts.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Diagnostics**
* Added installed Python package information to deterministic test runs,
including package versions, to make test environment details visible in
the output.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c5fa186](https://github.com/flashinfer-ai/flashinfer/commit/c5fa1868802e3ffc283d414c820df536c2f132c3)

- **作者**: lz
- **时间**: 2026-09-09T21:01:36Z
- **提交信息**: fix(jit): avoid invalidating bgmv_moe cache on source staging (#4798)

<!-- .github/pull_request_template.md -->

## 📌 Description

Every new process that JIT-loads `bgmv_moe` rebuilt all kernels from
scratch, even with a fully warm cache. `gen_bgmv_moe_module()` stages
its sources and headers into `FLASHINFER_GEN_SRC_DIR` with
`shutil.copy`, which stamps a fresh mtime on every copy. Since the JIT
path delegates `.so` freshness entirely to ninja's dependency scan
(`JitSpecNvcc.try_load()` returns `None` for non-AOT modules), the
re-staged inputs always looked newer than the cached objects, so ninja
recompiled the whole module on every warm start. #4782 reports 216–218 s
per process on Blackwell versus 4.3 s once mtimes are preserved (as
measured by the reporter).

**Fix:** stage with `shutil.copy2`, which preserves source mtimes, so
unchanged inputs stay older than the built artifact and ninja no-ops.
`shutil.copy` already propagated permission bits, so the only staging
behavior that changes is timestamp preservation.

**Regression test:** `tests/jit/test_bgmv_moe_jit_cache.py` is
deterministic and needs no GPU, nvcc, or sleeps. It runs
`gen_bgmv_moe_module()` against a fake csrc tree with fixed old mtimes
in a redirected workspace, simulates an already-built `.so` newer than
the sources, clears the `functools.cache` to model a fresh process,
re-stages, and asserts the JIT-cache freshness invariant: no staged
source/header may become newer than the existing build artifact. It
fails on current `main` (all 12 staged files get fresh mtimes) and
passes with this change.

**Validation**
- Regression test: fails on `main`, passes with the fix.
- `tests/jit/test_jit_cpp_ext.py`: 18 passed; the 3 failures reproduce
identically on unmodified `main` in my CPU-only environment (no CUDA
toolkit installed) and are unrelated to this change.
- Warm-cache ninja check over the actual staged output of
`gen_bgmv_moe_module()` (using a `cp` stand-in build graph, since nvcc
is unavailable locally): after re-staging unchanged sources, `ninja -n`
reports "no work to do" with this change, while on `main` it rebuilds
all targets.
- `pre-commit run --files <changed files>`: all hooks pass (mypy, ruff
check, ruff format, whitespace hooks).

## 🔍 Related Issues

Fixes #4782

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. *(ran `pre-commit run --files <changed
files>` instead — all hooks pass; see Reviewer Notes)*

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.). *(Targeted regression
and changed-file checks pass; 3 CUDA-toolkit-dependent failures
reproduce identically on unmodified main.)*

## Reviewer Notes

Hooks were run as `pre-commit run --files flashinfer/jit/bgmv_moe.py
tests/jit/test_bgmv_moe_jit_cache.py` (the changed files) rather than
`--all-files`, to avoid churning unrelated files. GPU kernel tests for
bgmv_moe were not run locally (no CUDA device available); the added
regression test is GPU-free by design.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved JIT compilation caching by preserving CUDA source and header
file timestamps.
* Prevented unnecessary full rebuilds when generating BGMV MoE modules
from unchanged files.

* **Tests**
* Added regression coverage to verify cached builds do not trigger
avoidable recompilation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4fa4252](https://github.com/flashinfer-ai/flashinfer/commit/4fa42525f67d1fa684f26c2fcbfa009e6e59dfe3)

- **作者**: eigen
- **时间**: 2026-09-09T20:33:44Z
- **提交信息**: feat(cake_kernel): add MiniMax-H3 MXFP8 pre-attention for SM100a/SM103a (#5060)

<!-- .github/pull_request_template.md -->

## 📌 Description

This adds a Cake-generated MiniMax-H3 MXFP8 pre-attention implementation
for
NVIDIA B200 (`sm_100a`) and B300 (`sm_103a`). Comparative measurements
used
FlashInfer revision `140919437374d14e51491435f96d4e70bebd5f68`; the
delivery
also includes the subsequent merge of `main` at
`8e3854bcec6e257cdfc674e579cff64018b86e63`. The generated sources and
operation
runtime were unchanged by that merge.

The prepared `MiniMaxH3Mxfp8PreAttention` operation composes two
generated stages
with FlashInfer's prepacked MXFP8 QKV GEMM:

`BF16 input → RMSNorm → indexed AdaLN → MXFP8 activation → QKV GEMM →
Q/K RMSNorm → split-half NeoX RoPE → destination-major MXFP8 output`

It preserves BF16 rounding points, E4M3 packed values, UE8M0 scale
bytes,
output layout, and caller-owned output objects. Each GPU architecture
has its
own generated binaries and exact shape routes. Setup binds caller-owned
intermediates and workspaces; the prepared run supports CUDA Graph
replay and
independent streams.

### Validation scope

All performance tables and the runtime, AOT, sanitizer, formatting, and
wheel
qualification receipts below describe the original delivery at
`a7ecfe97e01e64649e2d5f26106fe17a479975ef`. The subsequent host ABI
correction
has canonical source-equivalence and compilation evidence described
separately
below; those original qualification runs have not been repeated for it.

Each architecture covers 44 shapes: 24 production centers (six each for
P1, P2, P4, and P8), eight aligned neighbors, eight one-row tails, and
four
smoke shapes. Correctness compares exact packed values and scale bytes;
mathematical output uses `atol=rtol=0.1`, and BF16 Q/K intermediates use
`atol=rtol=1e-2`. Invalid AdaLN indices `-1`, `9`, `INT_MIN`, and
`INT_MAX`
must produce zero rows.

Both physical architectures passed all 44 frozen contract shapes:
**44/44 on B200 and 44/44 on B300**. Every row completed validation and
passed the exporter’s correctness and timing gates.

The tables below include all 88 final source/export comparisons,
including production centers, aligned neighbors, tails, and smoke
shapes. The timing ratio is selected-source latency divided by
exported-callable latency.

| Architecture | Shapes | Source/export geomean | Minimum ratio |
Maximum ratio |
|---|---:|---:|---:|---:|
| B200 / sm_100a | 44 | 1.058980649x | 1.002586148x | 1.499891622x |
| B300 / sm_103a | 44 | 1.067392449x | 1.003301495x | 1.540005600x |
| Combined | 88 | 1.063178230x | 1.002586148x | 1.540005600x |

#### B200 / sm_100a: all 44 source/export rows

| Shape | P | M | Source ms | Export ms | Source/export |
|---|---:|---:|---:|---:|---:|
| center_p1_4s_m33472 | 1 | 33472 | 4.483099000 | 4.451304000 |
1.007142851x |
| center_p2_4s_m16736 | 2 | 16736 | 2.461829500 | 2.430920500 |
1.012714937x |
| center_p4_4s_m8368 | 4 | 8368 | 1.122464000 | 1.089024500 |
1.030705921x |
| center_p8_4s_m4184 | 8 | 4184 | 0.637168000 | 0.583744500 |
1.091518635x |
| center_p1_5s_m38592 | 1 | 38592 | 5.153550500 | 5.120702000 |
1.006414843x |
| center_p2_5s_m19296 | 2 | 19296 | 2.925101500 | 2.894782000 |
1.010473846x |
| center_p4_5s_m9648 | 4 | 9648 | 1.258529000 | 1.227039500 |
1.025662988x |
| center_p8_5s_m4824 | 8 | 4824 | 0.697248500 | 0.644960500 |
1.081071632x |
| center_p1_6s_m48768 | 1 | 48768 | 6.522210000 | 6.486962000 |
1.005433668x |
| center_p2_6s_m24384 | 2 | 24384 | 3.290818000 | 3.260946000 |
1.009160532x |
| center_p4_6s_m12192 | 4 | 12192 | 1.666148000 | 1.635964000 |
1.018450284x |
| center_p8_6s_m6096 | 8 | 6096 | 0.844256000 | 0.794721000 |
1.062330050x |
| center_p1_8s_m58944 | 1 | 58944 | 7.866756000 | 7.832864500 |
1.004326833x |
| center_p2_8s_m29472 | 2 | 29472 | 4.533846500 | 4.499704500 |
1.007587609x |
| center_p4_8s_m14736 | 4 | 14736 | 2.227809500 | 2.197713500 |
1.013694233x |
| center_p8_8s_m7368 | 8 | 7368 | 0.991137500 | 0.950785000 |
1.042441246x |
| center_p1_10s_m74240 | 1 | 74240 | 9.853495500 | 9.818361500 |
1.003578397x |
| center_p2_10s_m37120 | 2 | 37120 | 5.531431000 | 5.496920000 |
1.006278243x |
| center_p4_10s_m18560 | 4 | 18560 | 2.544898000 | 2.513667000 |
1.012424478x |
| center_p8_10s_m9280 | 8 | 9280 | 1.211489000 | 1.180385000 |
1.026350725x |
| center_p1_15s_m109952 | 1 | 109952 | 14.703173000 | 14.665246500 |
1.002586148x |
| center_p2_15s_m54976 | 2 | 54976 | 7.364222500 | 7.330750000 |
1.004566040x |
| center_p4_15s_m27488 | 4 | 27488 | 4.115757500 | 4.086680500 |
1.007115066x |
| center_p8_15s_m13744 | 8 | 13744 | 1.831505500 | 1.801442500 |
1.016688293x |
| aligned_p1_5s_minus64_m38528 | 1 | 38528 | 5.174980000 | 5.142232500 |
1.006368343x |
| aligned_p1_5s_plus64_m38656 | 1 | 38656 | 5.185519500 | 5.154393000 |
1.006038829x |
| aligned_p2_5s_minus32_m19264 | 2 | 19264 | 2.968619500 | 2.938650000 |
1.010198390x |
| aligned_p2_5s_plus32_m19328 | 2 | 19328 | 2.976222500 | 2.944739500 |
1.010691268x |
| aligned_p4_5s_minus16_m9632 | 4 | 9632 | 1.256674000 | 1.225602000 |
1.025352439x |
| aligned_p4_5s_plus16_m9664 | 4 | 9664 | 1.265255000 | 1.234209500 |
1.025154157x |
| aligned_p8_5s_minus8_m4816 | 8 | 4816 | 0.699472000 | 0.646945500 |
1.081191538x |
| aligned_p8_5s_plus8_m4832 | 8 | 4832 | 0.700482000 | 0.648097500 |
1.080828116x |
| tail_p1_5s_minus1_m38591 | 1 | 38591 | 5.164564000 | 5.131154500 |
1.006511108x |
| tail_p1_5s_plus1_m38593 | 1 | 38593 | 5.179768500 | 5.146683500 |
1.006428412x |
| tail_p2_5s_minus1_m19295 | 2 | 19295 | 2.613201500 | 2.582030500 |
1.012072282x |
| tail_p2_5s_plus1_m19297 | 2 | 19297 | 2.612654500 | 2.580895000 |
1.012305615x |
| tail_p4_5s_minus1_m9647 | 4 | 9647 | 1.260698000 | 1.230306000 |
1.024702798x |
| tail_p4_5s_plus1_m9649 | 4 | 9649 | 1.256229500 | 1.225636000 |
1.024961326x |
| tail_p8_5s_minus1_m4823 | 8 | 4823 | 0.697169000 | 0.644927000 |
1.081004517x |
| tail_p8_5s_plus1_m4825 | 8 | 4825 | 0.699267000 | 0.646273500 |
1.081998566x |
| smoke_p8_m1 | 8 | 1 | 0.200672000 | 0.133791000 | 1.499891622x |
| smoke_p8_m127 | 8 | 127 | 0.206912000 | 0.139456000 | 1.483708123x |
| smoke_p8_m128 | 8 | 128 | 0.207839000 | 0.140128000 | 1.483208210x |
| smoke_p8_m129 | 8 | 129 | 0.208702000 | 0.147264000 | 1.417196328x |

#### B300 / sm_103a: all 44 source/export rows

| Shape | P | M | Source ms | Export ms | Source/export |
|---|---:|---:|---:|---:|---:|
| center_p1_4s_m33472 | 1 | 33472 | 4.073497500 | 4.032525500 |
1.010160382x |
| center_p2_4s_m16736 | 2 | 16736 | 2.078369500 | 2.044099500 |
1.016765329x |
| center_p4_4s_m8368 | 4 | 8368 | 1.042025000 | 0.994124000 |
1.048184130x |
| center_p8_4s_m4184 | 8 | 4184 | 0.607574500 | 0.548038000 |
1.108635715x |
| center_p1_5s_m38592 | 1 | 38592 | 4.689873500 | 4.655697000 |
1.007340791x |
| center_p2_5s_m19296 | 2 | 19296 | 2.395214500 | 2.361678000 |
1.014200285x |
| center_p4_5s_m9648 | 4 | 9648 | 1.169884500 | 1.129532000 |
1.035724973x |
| center_p8_5s_m4824 | 8 | 4824 | 0.666359000 | 0.609109500 |
1.093988848x |
| center_p1_6s_m48768 | 1 | 48768 | 5.922045000 | 5.888610500 |
1.005677825x |
| center_p2_6s_m24384 | 2 | 24384 | 3.002790500 | 2.969599000 |
1.011177098x |
| center_p4_6s_m12192 | 4 | 12192 | 1.491277500 | 1.457342000 |
1.023285886x |
| center_p8_6s_m6096 | 8 | 6096 | 0.796360500 | 0.737016500 |
1.080519229x |
| center_p1_8s_m58944 | 1 | 58944 | 7.168885500 | 7.132402000 |
1.005115177x |
| center_p2_8s_m29472 | 2 | 29472 | 3.615700000 | 3.573750500 |
1.011738229x |
| center_p4_8s_m14736 | 4 | 14736 | 2.023061500 | 1.989812000 |
1.016709870x |
| center_p8_8s_m7368 | 8 | 7368 | 0.930633500 | 0.877894500 |
1.060074417x |
| center_p1_10s_m74240 | 1 | 74240 | 8.931281000 | 8.891228500 |
1.004504721x |
| center_p2_10s_m37120 | 2 | 37120 | 4.526374500 | 4.486783000 |
1.008824028x |
| center_p4_10s_m18560 | 4 | 18560 | 2.512362500 | 2.479203500 |
1.013374860x |
| center_p8_10s_m9280 | 8 | 9280 | 1.129503000 | 1.085130500 |
1.040891395x |
| center_p1_15s_m109952 | 1 | 109952 | 13.207191500 | 13.163731500 |
1.003301495x |
| center_p2_15s_m54976 | 2 | 54976 | 6.657553500 | 6.620771500 |
1.005555546x |
| center_p4_15s_m27488 | 4 | 27488 | 3.364929000 | 3.330014000 |
1.010484941x |
| center_p8_15s_m13744 | 8 | 13744 | 1.743890000 | 1.710866000 |
1.019302505x |
| aligned_p1_5s_minus64_m38528 | 1 | 38528 | 4.674936500 | 4.643217000 |
1.006831363x |
| aligned_p1_5s_plus64_m38656 | 1 | 38656 | 4.687437000 | 4.653609000 |
1.007269197x |
| aligned_p2_5s_minus32_m19264 | 2 | 19264 | 2.382656500 | 2.349328000 |
1.014186397x |
| aligned_p2_5s_plus32_m19328 | 2 | 19328 | 2.391065500 | 2.358951500 |
1.013613675x |
| aligned_p4_5s_minus16_m9632 | 4 | 9632 | 1.169536500 | 1.131981000 |
1.033176794x |
| aligned_p4_5s_plus16_m9664 | 4 | 9664 | 1.171743000 | 1.133918500 |
1.033357336x |
| aligned_p8_5s_minus8_m4816 | 8 | 4816 | 0.658856000 | 0.603367000 |
1.091965586x |
| aligned_p8_5s_plus8_m4832 | 8 | 4832 | 0.657767000 | 0.602886000 |
1.091030477x |
| tail_p1_5s_minus1_m38591 | 1 | 38591 | 4.682974000 | 4.651591000 |
1.006746724x |
| tail_p1_5s_plus1_m38593 | 1 | 38593 | 4.686842500 | 4.653023500 |
1.007268177x |
| tail_p2_5s_minus1_m19295 | 2 | 19295 | 2.381799000 | 2.349533000 |
1.013732942x |
| tail_p2_5s_plus1_m19297 | 2 | 19297 | 2.621001000 | 2.588857500 |
1.012416095x |
| tail_p4_5s_minus1_m9647 | 4 | 9647 | 1.168218500 | 1.133258500 |
1.030849096x |
| tail_p4_5s_plus1_m9649 | 4 | 9649 | 1.167212000 | 1.132699500 |
1.030469246x |
| tail_p8_5s_minus1_m4823 | 8 | 4823 | 0.658314000 | 0.603062000 |
1.091619104x |
| tail_p8_5s_plus1_m4825 | 8 | 4825 | 0.657031000 | 0.602118000 |
1.091199732x |
| smoke_p8_m1 | 8 | 1 | 0.242016500 | 0.157153000 | 1.540005600x |
| smoke_p8_m127 | 8 | 127 | 0.248818500 | 0.162881000 | 1.527609113x |
| smoke_p8_m128 | 8 | 128 | 0.249986000 | 0.163617000 | 1.527873021x |
| smoke_p8_m129 | 8 | 129 | 0.250370000 | 0.168578000 | 1.485187866x |

### Measurement protocol

Measurements pair the complete exported callable with the complete
segmented
FlashInfer callable using identical operands, preallocated outputs,
direct
launches, and CUPTI activity tracing with cold-L2 flushing. The
segmented
reference explicitly selects FlashInfer's CUDA RMSNorm implementation.
Compilation, allocation, weight packing, and communication are outside
the
timed region.

A separate paired comparison verifies export fidelity against the
selected
source for all 44 shapes per architecture. The frozen protocol uses
three
groups, 50 ms warmup and 250 ms measurement per arm, source/export
speedup
at least 0.97, endpoint drift at most 5%, and directional disagreement
at
most 5%.

## FlashInfer segmented MXFP8 baseline

Speedup is `baseline_ms / export_ms`; all values below come from the
paired CUPTI measurements.

| Arch | P | M | Shape | Set | Baseline ms | Export ms | Speedup |
|---|---:|---:|---|---|---:|---:|---:|
| sm_100a | 1 | 33472 | center_p1_4s_m33472 | P1 | 17.170864500 |
4.451304000 | 3.857490861x |
| sm_100a | 1 | 38592 | center_p1_5s_m38592 | P1 | 19.792793000 |
5.120702000 | 3.865249921x |
| sm_100a | 1 | 48768 | center_p1_6s_m48768 | P1 | 24.979839500 |
6.486962000 | 3.850776296x |
| sm_100a | 1 | 58944 | center_p1_8s_m58944 | P1 | 30.309445500 |
7.832864500 | 3.869522510x |
| sm_100a | 1 | 74240 | center_p1_10s_m74240 | P1 | 38.115621000 |
9.818361500 | 3.882075538x |
| sm_100a | 1 | 109952 | center_p1_15s_m109952 | P1 | 57.372931000 |
14.665246500 | 3.912169564x |
| sm_100a | 2 | 16736 | center_p2_4s_m16736 | primary | 8.901009500 |
2.430920500 | 3.661579842x |
| sm_100a | 2 | 19296 | center_p2_5s_m19296 | primary | 10.368456000 |
2.894782000 | 3.581774379x |
| sm_100a | 2 | 24384 | center_p2_6s_m24384 | primary | 12.690648500 |
3.260946000 | 3.891707652x |
| sm_100a | 2 | 29472 | center_p2_8s_m29472 | primary | 15.902909500 |
4.499704500 | 3.534211969x |
| sm_100a | 2 | 37120 | center_p2_10s_m37120 | primary | 19.850986000 |
5.496920000 | 3.611292506x |
| sm_100a | 2 | 54976 | center_p2_15s_m54976 | primary | 28.460062500 |
7.330750000 | 3.882285237x |
| sm_100a | 4 | 8368 | center_p4_4s_m8368 | primary | 4.403969500 |
1.089024500 | 4.043958148x |
| sm_100a | 4 | 9648 | center_p4_5s_m9648 | primary | 5.038275500 |
1.227039500 | 4.106041819x |
| sm_100a | 4 | 12192 | center_p4_6s_m12192 | primary | 6.404449000 |
1.635964000 | 3.914786022x |
| sm_100a | 4 | 14736 | center_p4_8s_m14736 | primary | 7.930785000 |
2.197713500 | 3.608652811x |
| sm_100a | 4 | 18560 | center_p4_10s_m18560 | primary | 9.705549000 |
2.513667000 | 3.861111675x |
| sm_100a | 4 | 27488 | center_p4_15s_m27488 | primary | 14.726687500 |
4.086680500 | 3.603581807x |
| sm_100a | 8 | 4184 | center_p8_4s_m4184 | primary | 2.289442000 |
0.583744500 | 3.921993269x |
| sm_100a | 8 | 4824 | center_p8_5s_m4824 | primary | 2.601428000 |
0.644960500 | 4.033468716x |
| sm_100a | 8 | 6096 | center_p8_6s_m6096 | primary | 3.246530500 |
0.794721000 | 4.085119809x |
| sm_100a | 8 | 7368 | center_p8_8s_m7368 | primary | 3.889092500 |
0.950785000 | 4.090401616x |
| sm_100a | 8 | 9280 | center_p8_10s_m9280 | primary | 4.865856000 |
1.180385000 | 4.122261804x |
| sm_100a | 8 | 13744 | center_p8_15s_m13744 | primary | 7.159307000 |
1.801442500 | 3.974207892x |
| sm_103a | 1 | 33472 | center_p1_4s_m33472 | P1 | 16.463247000 |
4.032525500 | 4.082614481x |
| sm_103a | 1 | 38592 | center_p1_5s_m38592 | P1 | 18.988434500 |
4.655697000 | 4.078537435x |
| sm_103a | 1 | 48768 | center_p1_6s_m48768 | P1 | 23.958213500 |
5.888610500 | 4.068568213x |
| sm_103a | 1 | 58944 | center_p1_8s_m58944 | P1 | 29.069210500 |
7.132402000 | 4.075655088x |
| sm_103a | 1 | 74240 | center_p1_10s_m74240 | P1 | 36.504875000 |
8.891228500 | 4.105717787x |
| sm_103a | 1 | 109952 | center_p1_15s_m109952 | P1 | 54.135115000 |
13.163731500 | 4.112444484x |
| sm_103a | 2 | 16736 | center_p2_4s_m16736 | primary | 8.397272000 |
2.044099500 | 4.108054427x |
| sm_103a | 2 | 19296 | center_p2_5s_m19296 | primary | 9.673045000 |
2.361678000 | 4.095835673x |
| sm_103a | 2 | 24384 | center_p2_6s_m24384 | primary | 12.192460500 |
2.969599000 | 4.105759902x |
| sm_103a | 2 | 29472 | center_p2_8s_m29472 | primary | 14.719167500 |
3.573750500 | 4.118689175x |
| sm_103a | 2 | 37120 | center_p2_10s_m37120 | primary | 18.503726500 |
4.486783000 | 4.124052021x |
| sm_103a | 2 | 54976 | center_p2_15s_m54976 | primary | 27.254230000 |
6.620771500 | 4.116473435x |
| sm_103a | 4 | 8368 | center_p4_4s_m8368 | primary | 4.251357000 |
0.994124000 | 4.276485630x |
| sm_103a | 4 | 9648 | center_p4_5s_m9648 | primary | 4.874064500 |
1.129532000 | 4.315118562x |
| sm_103a | 4 | 12192 | center_p4_6s_m12192 | primary | 6.144567000 |
1.457342000 | 4.216283480x |
| sm_103a | 4 | 14736 | center_p4_8s_m14736 | primary | 7.616930500 |
1.989812000 | 3.827964903x |
| sm_103a | 4 | 18560 | center_p4_10s_m18560 | primary | 9.513932500 |
2.479203500 | 3.837495591x |
| sm_103a | 4 | 27488 | center_p4_15s_m27488 | primary | 13.730510000 |
3.330014000 | 4.123258941x |
| sm_103a | 8 | 4184 | center_p8_4s_m4184 | primary | 2.228278500 |
0.548038000 | 4.065919699x |
| sm_103a | 8 | 4824 | center_p8_5s_m4824 | primary | 2.524252000 |
0.609109500 | 4.144167838x |
| sm_103a | 8 | 6096 | center_p8_6s_m6096 | primary | 3.143072000 |
0.737016500 | 4.264588378x |
| sm_103a | 8 | 7368 | center_p8_8s_m7368 | primary | 3.767046000 |
0.877894500 | 4.291000798x |
| sm_103a | 8 | 9280 | center_p8_10s_m9280 | primary | 4.705948500 |
1.085130500 | 4.336758113x |
| sm_103a | 8 | 13744 | center_p8_15s_m13744 | primary | 6.973269000 |
1.710866000 | 4.075870933x |

### Per-architecture partition geomeans and latency sums

| Arch / partition | Shapes | Baseline sum ms | Export sum ms | Geomean
speedup |
|---|---:|---:|---:|---:|
| sm_100a / P1 | 6 | 187.741494500 | 48.375440500 | 3.872828814x |
| sm_100a / P2 | 6 | 96.174072000 | 25.914023000 | 3.691120928x |
| sm_100a / P4 | 6 | 48.209715500 | 12.750089000 | 3.851426815x |
| sm_100a / P8 | 6 | 24.051656000 | 5.956038500 | 4.037294279x |
| sm_103a / P1 | 6 | 179.119095500 | 43.764195000 | 4.087224554x |
| sm_103a / P2 | 6 | 90.739901500 | 22.056681500 | 4.111466810x |
| sm_103a / P4 | 6 | 46.131361500 | 11.380027500 | 4.094595453x |
| sm_103a / P8 | 6 | 23.341866000 | 5.568055000 | 4.195041341x |

### Per-architecture aggregate geomeans and latency sums

| Arch / set | Shapes | Baseline sum ms | Export sum ms | Geomean
speedup |
|---|---:|---:|---:|---:|
| sm_100a / primary | 18 | 168.435443500 | 44.620150500 | 3.857359443x |
| sm_100a / P1 | 6 | 187.741494500 | 48.375440500 | 3.872828814x |
| sm_100a / all | 24 | 356.176938000 | 92.995591000 | 3.861220983x |
| sm_103a / primary | 18 | 160.213129000 | 39.004764000 | 4.133468933x |
| sm_103a / P1 | 6 | 179.119095500 | 43.764195000 | 4.087224554x |
| sm_103a / all | 24 | 339.332224500 | 82.768959000 | 4.121859016x |

### Combined geomeans and latency sums

| Set | Shapes | Baseline sum ms | Export sum ms | Geomean speedup |
|---|---:|---:|---:|---:|
| primary | 36 | 328.648572500 | 83.624914500 | 3.993028352x |
| P1 | 12 | 366.860590000 | 92.139635500 | 3.978582790x |
| all | 48 | 695.509162500 | 175.764550000 | 3.989412052x |

### CUPTI activity and sample totals

The totals cover the 48 production rows. GPU span sums come from the
final per-shape CUPTI receipts and include gaps between kernels; they
are not kernel-active duration. Warmup and pilot samples are excluded.

| Arch | Arm | Samples | Activity records | Launch records | Kernel
records | Accumulated GPU span ms |
|---|---|---:|---:|---:|---:|---:|
| sm_100a | baseline | 12156 | 607952 | 607952 | 607952 | 87855.924047 |
| sm_100a | export | 12156 | 60780 | 60780 | 60780 | 22731.953655 |
| sm_103a | baseline | 13244 | 661398 | 661398 | 661398 | 93423.990568 |
| sm_103a | export | 13244 | 66220 | 66220 | 66220 | 22687.750727 |
| combined | baseline | 25400 | 1269350 | 1269350 | 1269350 |
181279.914615 |
| combined | export | 25400 | 127000 | 127000 | 127000 | 45419.704382 |

### Physical turnaround of final export steps

These measured durations cover the supplied successful managed export
steps. Earlier preparation, tests, retries, and allocation wait are
outside this scope.

| Arch | Physical elapsed s |
|---|---:|
| sm_100a | 3373.854 |
| sm_103a | 2136.194 |
| Sum of final step durations | 5510.048 |
| Earliest step start through latest completion | 3376.747 |

The observed export-and-validation workflow ran from
`2026-09-09T05:25:48+00:00` through
`2026-09-09T12:53:50+00:00`, totaling **26,882.070 seconds**
(7 h 28 min 2.1 s).
This broader interval includes preparation, retries, and validation; it
is
separate from the successful export-step interval above.
The endpoint records the original qualification workflow; the subsequent
host
ABI correction and CI follow-up occurred after this recorded interval.

Including the compatibility correction, CI, and final report
preparation,
the observed end-to-end interval from `2026-09-09T05:25:48.827948Z`
through
`2026-09-09T16:14:46.698962Z` is **38,937.871014 seconds**.
This includes waiting and retries; it is separate from the measured GPU
latencies and accumulated CUPTI spans above.

## 🔍 Related Issues

Tracks #4532, candidate 2A: MXFP8 pre-attention for B200 (`sm_100a`) and
B300 (`sm_103a`). Implementation status is tracked in the issue; its
other kernel candidates remain open.

Also tracked in #4254, the long-term CAKE-generated kernel progress
tracker.

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

Changed-file hooks passed using `pre-commit run --files` with the
complete
changed-file list, including mypy and Ruff checks and formatting. The
352
generated C/CUDA source checksums were unchanged during that formatting
run.
The full-repository `--all-files` checkbox is left unchecked because the
executed check targeted the changed files.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Targeted runtime tests passed on both B200 and B300:

```bash
python -m pytest -q tests/test_minimax_h3_mxfp8.py -rA
```

Each architecture passed all 11 tests without skips (B200: 14.87 s;
B300: 3.35 s). Coverage includes exact dispatch, invalid AdaLN indices,
caller-owned output identity, poisoned-output CUDA Graph replay, and
independent streams with valid nonzero and invalid zero workloads.

The AOT integration built and loaded all 88 generated modules per
architecture, then successfully launched all 44 routes using those AOT
modules. These checks use FlashInfer's native `build_jit_specs`,
`copy_built_kernels`, `is_aot`, and `try_load` paths.


Compute Sanitizer `--tool synccheck` passed on B200 and B300, with
`ERROR SUMMARY: 0 errors` on each. Both runs covered all 44 routes,
invalid-index behavior, CUDA Graph replay, and independent streams.
The validation payload took 1,656.687 seconds on B200 and 1,715.271
seconds
on B300.

Separate Compute Sanitizer `--tool racecheck` runs also passed on both
architectures: `RACECHECK SUMMARY: 0 hazards displayed (0 errors, 0
warnings)`.
Each run covered all 44 routes, invalid-index behavior, CUDA Graph
replay,
and independent streams. B200's validation payload took 5,661.901
seconds
(5,742.467 seconds for the complete task); B300's took 6,270.145 seconds
(6,332.620 seconds for the complete task).

Built-wheel validation passed for
`flashinfer_python-0.6.18-py3-none-any.whl`
from the original qualified delivery. All 352 generated C/CUDA files in
that
wheel matched that delivery's sealed source checksums.
A fresh interpreter outside the source checkout imported the installed
public
API and resolved all sources from the installed package: 44 shapes, 88
JIT
specifications, and 176 generated source files for each architecture.
The combined formatting and wheel-validation task took 1,018.152
seconds.

### Host ABI correction and CI follow-up

The original PR CI run failed in `AOT Build Import (arm64, cu129)`
because an
exact alignment assertion also applied to the CUDA toolkit's host type.
The
repair limits that assertion to the locally declared NVRTC type.

Canonical regeneration passed for the complete delivery: all 176 device
kernel bodies and all 176 bindings are unchanged, with 44 routes per
architecture and unchanged route and ABI fields. Source and closure
hashes
were regenerated canonically for the corrected sources, and both frozen
protocols passed their semantic checks. The regeneration and validation
task
completed in 99.151 seconds; all 14 identity/lowering unit tests passed
in
2.54 seconds.

CUDA 12.9 compilation now passes for four representative norm/post
kernels;
the four original versions failed the expected assertion. With CUDA
13.3,
old and corrected versions produced exactly matching SASS for all four
representative kernels.

The corrected public revision is
`1c0a7793021cccd8dfe1a301f37780641c3b23a6`. The original compilation
failure is resolved. [Full PR
Test](https://github.com/flashinfer-ai/flashinfer/actions/runs/34360906518)
passed all 11 GPU/AOT matrix jobs: CUDA 12.9 and 13.0 AOT build/import
on
x64 and arm64, five A10G test shards, T4 tests, and H100 tests. The
summary,
pre-commit, PR documentation checks, and documentation build also passed
at this revision. The full CI run took 7,623 seconds (2 h 7 min 3 s),
from `2026-09-09T14:01:47Z` through `2026-09-09T16:08:50Z`.

## 🔬 Experimental Track

This is not an experimental-track change. The default template block
below is
intentionally left unchanged, with the experimental checkbox unchecked.

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

The generated stages preserve the selected implementation's numerical
behavior and exact dispatch. The public API, route inventory, AOT
integration,
and runtime tests are included in this change.

The native AOT receipts record all 88 loaded module specification
identities
per architecture. The sanitizer runs loaded those same prepared AOT
modules
and native GEMM tactic configurations. Both sanitizer commands used the
same
complete route and runtime-check coverage. The host ABI correction
preserves
the complete device bodies, bindings, routes, and ABI; its compilation
checks
and successful CI results are described above.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [cac5690](https://github.com/flashinfer-ai/flashinfer/commit/cac5690a9341800578e0155f9e990652ea849bd3)

- **作者**: Aaron Eichler
- **时间**: 2026-09-09T19:59:12Z
- **提交信息**: fix(bench): use float32 cos_sin_cache in apply_rope_with_cos_sin_cache (#5066)

## Summary
- `testApplyRopeWithCosSinCache` allocated `cos_sin_cache` with
`input_dtype` (fp16/bf16), but
`flashinfer.rope.apply_rope_with_cos_sin_cache` requires float32 and
raised before any timing.
- Allocate the cache as `torch.float32` and count it as 4 bytes/elem in
`problem_bytes`.

Fixes #5025

## Test plan
- [x] DGX Spark (GB10): issue repro with `--input_dtype float16` ->
`[PERF] median 1.571 ms` (no `cos_sin_cache should be float32`)
- [x] Same with `--input_dtype bfloat16` -> `[PERF] median 1.572 ms`

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Benchmarks**
- Updated rotary-position-embedding benchmark calculations to use the
required 32-bit floating-point cache format.
- Adjusted memory-bandwidth measurements to accurately reflect the
cache’s fixed 4-byte element size.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Aaron Eichler <319454444+aeichler-ac@users.noreply.github.com>

### [0365890](https://github.com/flashinfer-ai/flashinfer/commit/0365890b7e0f49304f246e5dc8391aec93536fa0)

- **作者**: Harris Nover
- **时间**: 2026-09-09T19:32:44Z
- **提交信息**: Replayssm prefix materialize (#4815)

<!-- .github/pull_request_template.md -->

## 📌 Description

For ReplaySSM, instead of keeping an up-to-date SSM state, we instead
keep a historical state and store the inputs since in a buffer. When the
buffer fills up, we "flush" it into an updated state. See
checkpointing_ssu.cu and related files in this repo.

Because prefill is not aware of the ReplaySSM buffer, for prefix caching
to work we need to materialize the state at arbitrary tokens. This
shouldn't be done as part of checkpointing_ssu.cu because that can't
output an updated state until the next step, and we want to do it at the
end of the current step, after we know how many tokens were accepted
(for the MTP case).

Note we don't apply all the accepted tokens. For example, we may save
states that are multiples of 512 tokens, so if our last state is
materialized state is at 508 and our buffer represents another 7, then
we only want to apply 4 of the tokens in our state update. And that is
independent of whether the 7 came from accepting 7 this step, or
accepting fewer over the course of a few steps since our last
checkpointing.

This PR provides the necessary kernel and wrapping to allow that state
materialization. The main differences from checkpointing_ssu are:
- No new input or output tokens, we just use the old state, the ring
buffer and its metadata.
- Does not update any of those inputs, rather it writes out new state to
a provided location.
- Applies a user-given # of tokens, rather than all tokens in the
buffer.
- Runs on all layers at once, to minimize launches. This means most of
our inputs are actually per-layer tables of pointers, slots, etc.
 - Persistent kernels (see next).

We do make extensive use of the helper function's in checkpointing_ssu's
nicely modular code, so not much needed writing. This probably comes
with some inefficiencies (helper functions naturally want to process
input or produce output tokens), but we hope dead code elimination
mostly covers it. And as this runs infrequently a few % inefficient is
not a big deal.

One unexpected wrinkle was that to avoid host/device sync, we expect to
normally be invoked for all requests in the latest batch, with -1 as the
flag for not needing to materialize. For large batches and large models
like Nemotron v3 Ultra, a naive kernel approach would then spend over a
millisecond every forward pass just to launch nearly empty CTAs that do
nothing, which would be a material loss. Instead we adopt persistent
kernels and require the user to pass in an additional batch-sized tensor
that is the indices in the batch of requests that need flushing, and -1
thereafter. This lets us minimize the no-write case to 2 microseconds on
a B300, even for nemo ultra v3 TP=1 (48 layers, 256 heads/layer, mamba-2
dim 64x128) at batch size 256. With that setup, each actual request
whose state is written costs about 70-80 additional micros.

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

This is my first FlashInfer PR, so I may have messed up some plumbing,
missed some typically updated file. For example I missed the rst the
first time around. I attempted to have my agent audit for gaps though.

AI (codex) was used, but I have reviewed every line.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added `replayssm_materialize` to the public Mamba API for efficiently
materializing ReplaySSM prefix states.
- Supports active-request selection, multilayer and grouped-head
configurations, zero-length prefixes, and persistent GPU execution.
- Supports BF16, FP16, INT8, and FP8 state workflows, including optional
stochastic replay and state scaling.
- Added optional dependency anchors for improved `torch.compile`
integration.

- **Documentation**
  - Added `replayssm_materialize` to the Mamba API documentation.

- **Benchmarks**
- Added configurable performance benchmarking with CUDA event, CUPTI,
and CUDA Graph timing modes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Harris Nover <249353502+hnover-nv@users.noreply.github.com>

### [3985489](https://github.com/flashinfer-ai/flashinfer/commit/3985489542af7adba88b970e634cf7490d72ff63)

- **作者**: Yuxian Qiu
- **时间**: 2026-09-09T19:12:53Z
- **提交信息**: refactor(attention): unify PrimTS plan/run and page-table contracts (#4829)

## 📌 Description

Refactor the experimental PrimTS context, decode, and MLA APIs around
one consistent `plan()`/`run()` ownership rule. The goal is to let an
LLM inference framework cache a wrapper by its static execution profile
and reuse it across requests without rebuilding the plan whenever
request metadata changes. This is the FlashInfer-side prerequisite for
[NVIDIA/TensorRT-LLM#17399](https://github.com/NVIDIA/TensorRT-LLM/pull/17399).

### Static planning and request-varying runs

- `plan()` defines the static profile used to select or compile a kernel
and size its resources: device, exact batch profile, maximum Q/KV
capacities, head and page geometry, dtypes, packed/fixed query storage,
and mask/window specialization policy.
- `run()` receives all data that may change from request to request:
query/KV tensors, page tables, sequence lengths, packed-query offsets,
variable-window bounds, scale overrides, and optional output tensors.

Plans may retain defaults or resources whose addresses must remain
stable rather than use them as compilation discriminators. Context plans
retain default scale tensors and allocation-free variable-window
scratch; decode and MLA plans bind caller-owned or private workspace. A
failed re-plan does not replace the last complete plan.

`BatchPrefillTSWrapper` now follows the same contract as
`BatchPrefillPagedTSWrapper`: planning is keyword-only and based on
maximum capacities, while fixed or packed request tensors and metadata
are supplied to `run()`. Packed offsets, request totals, and
variable-window bounds can change between launches within the planned
profile. Planning and warmup occur outside CUDA Graph capture, and a
successful re-plan invalidates captures made from the previous plan.
Before using a CUDA stream that is not already ordered after the
planning stream, the caller must establish that dependency.

Decode's optional CPU `seq_lens` plan argument is specialization
evidence only. When supplied, validated runs must preserve the proven
length mode; omit it for fully dynamic sequence-length reuse. Every
launch still receives the current device sequence lengths.

Validation remains enabled by default. Trusted framework integrations
may use `validate=False` only after guaranteeing the complete dtype,
device, shape, stride, alignment, value, aliasing, and lifetime
contract, avoiding host synchronization in steady-state execution and
CUDA Graph replay.

The benchmark adapters use packed-query storage for PrimTS decode and
MLA (`packed_query=True`) with preallocated output and `validate=False`.
Existing CUDA Graph, CUPTI, cold-L2, workspace, scale, mask/window, and
automatic scheduling settings remain enabled.

### Unified fixed-row page metadata

Reusable paged context, decode, and MLA paths use the same
request-varying metadata:

- `block_tables`: an `int32` CUDA tensor with shape `[B, C]`, unit inner
stride, and a non-overlapping row stride;
- `seq_lens` / `seq_lens_kv`: contiguous `int32` CUDA sequence lengths
with shape `[B]`.

For request `b`, logical page `p` resolves as `block_tables[b, p]`. Only
the prefix required by the current sequence length is active, so
inactive capacity columns are ignored. Compact `(C, 1)` tables and
row-padded views such as `[B, 2, C][:, 0, :]` with stride `(2*C, 1)` are
accepted directly.

The PrimTS one-shot APIs now use that same contract instead of a CSR
triplet:

- `batch_prefill_with_paged_kv_cache(..., qo_indptr, block_tables,
seq_lens_kv, ...)`
- `batch_decode_with_paged_kv_cache(..., block_tables, seq_lens_kv,
...)`

The decode trace schema, examples, and generated fixture are updated
accordingly. Decode and MLA wrapper trace constraints also describe the
runtime bounds enforced by the APIs. The separate generic FlashInfer
decode adapter retains its existing CSR-to-fixed-table compatibility
path.

### MLA public API naming

The MLA helpers now use a consistent `batch_mla_decode` name:

| Previous name | New name |
|---|---|
| `batch_decode_mla_with_paged_kv_cache` |
`batch_mla_decode_with_paged_kv_cache` |
| `get_prims_ts_batch_decode_mla_workspace_size` |
`get_prims_ts_batch_mla_decode_workspace_size` |
| `prims_ts_batch_decode_with_kv_cache_mla` |
`prims_ts_batch_mla_decode_with_kv_cache` |

These are hard renames; the old aliases are not retained. Public
exports, lazy MLA exports, documentation, tests, trace examples, and
`fi_api` tags use the new names.

## 🔍 Related Issues

Follow-up to #4357 and prerequisite for
[NVIDIA/TensorRT-LLM#17399](https://github.com/NVIDIA/TensorRT-LLM/pull/17399).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [ ] I have installed the hooks with `pre-commit install`.
- [x] Applicable pre-commit hooks, mypy, Ruff check/format, Python
compilation, and diff checks passed.

## 🧪 Tests

- [x] Context suite: `100 passed`, `81 skipped` on the local
non-Blackwell host.
- [x] Decode suite: `97 passed`, `88 skipped`.
- [x] MLA suite: `15 passed`, `84 skipped`.
- [x] Trace-template consistency: `759 passed`.
- [x] PrimTS benchmark contract tests: `15 passed`.
- [x] B200/SM100 focused matrix on the preceding implementation
snapshot: `9 passed`, `0 skipped`. Two cases specifically covered the
plan-stream readiness machinery removed by this follow-up; the remaining
cases covered dynamic packed offsets, variable-window and fixed-table
CUDA Graph replay, fixed-table one-shot context, and decode/MLA public
parity. No current-head performance result is claimed.
- [x] Independent final staged review found no P0-P2 issues.

## Reviewer Notes

Please focus on whether each argument belongs to the static
compilation/resource profile in `plan()` or the request-varying launch
state in `run()`, and whether the resulting wrappers are safe to cache
and reuse across requests and CUDA Graph replays under the documented
caller-managed stream and lifetime contract.

---------

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>
Signed-off-by: Yuxian Qiu <yuxianq@nvidia.com>

### [b51a65a](https://github.com/flashinfer-ai/flashinfer/commit/b51a65a27f49cf0b31061cf9e42bc09e51c71696)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-09T19:03:57Z
- **提交信息**: fix(mla): prevent intermittent hang in SM120 sparse-MLA swapAB prefill on DGX Spark (#5048)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Fixes the intermittent `test_sparse_mla_sm120` hang on Spark CI (#5001).

The swapAB prefill kernel (#4802) runs 4 IO warps, but only `BI` IO
threads gather (`BI=64` for DSv3.2, 32 for DOTS3_SWA). IO threads with
`io_tid >= BI` do no work and no barrier counts them, yet they still
spin on `mbarrier_wait_parity` each tile. Since the pipeline's phases
advance without them, a spectator warp starved past a full phase window
near kernel drain waits on a parity that never completes again and spins
forever — the CTA never retires. A cuda-gdb autopsy of a live hang
confirms it: the whole grid drained except one spectator IO warp
spinning at the wait.

Matches the symptoms: intermittent (~2% per launch of the worst shape),
worst at `num_heads=128` (max occupancy pressure), and absent from the
mg impl (every thread participates in its barriers).

**Fix:** retire spectator IO threads before the pipeline loop (`if
(io_tid >= BI) return;`) — they have no work after the block-wide sync.

## 🔍 Related Issues

<!-- Link any related issues here -->

#5001

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

## Summary by CodeRabbit

* **Bug Fixes**
* Improved sparse attention prefill stability by preventing inactive
processing threads from waiting indefinitely during kernel completion.


<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [534b4d8](https://github.com/flashinfer-ai/flashinfer/commit/534b4d8bc6c6b850e937a5e9c3f280f7c077dfac)

- **作者**: Aaron Eichler
- **时间**: 2026-09-09T18:24:51Z
- **提交信息**: fix(attention): enable SM121 FMHA v2 prefill (#4661)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enable `fmha_v2_prefill_sm120` on SM121 after validating the existing
kernel on an NVIDIA DGX Spark with a GB10 GPU.

`is_sm12x_supported` continues to enforce the minimum CUDA version. The
explicit `(12, 0)` and `(12, 1)` list limits execution to validated
SM12x variants.

The JIT prebuild collector is updated because selecting the direct
SM120/SM121 tests previously caused the module to compile after the
prebuild stage.

## 🔍 Related Issues

Fixes #4600.
Alternative to #4606.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run `pre-commit run --all-files`.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing.

Targeted validation:

`pytest tests/attention/test_fmha_v2_prefill.py -v -k
"test_fmha_v2_prefill_sm120"`

Result:

`26 passed, 2462 deselected`

Hardware:

- NVIDIA DGX Spark
- NVIDIA GB10
- Compute capability 12.1
- CUDA 13.0
- PyTorch 2.13.0+cu130

Numerical comparisons passed within the existing test tolerances.
Device-scale, CUDA Graph, validation, and async-enqueue cases passed.

## Reviewer Notes

The 26 tests affected by #4600 pass on SM121.

A local full-file run was stopped during the existing DeepSeek
`seq_len=8192` case after the Spark became unresponsive. That path was
already enabled on SM121 and is not changed by this PR.

Please run the internal `unit_test_spark` matrix for
`tests/attention/test_fmha_v2_prefill.py` on cu129 and cu130.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for FMHA v2 prefill operations on SM121 GPUs alongside
SM120.
  * Expanded compatible GPU detection for supported prefill workloads.

* **Bug Fixes**
* Updated GPU compatibility messaging to accurately reflect supported
hardware.
* Improved setup for relevant FMHA v2 prefill scenarios, ensuring
supported tests are enabled and recognized correctly.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Aaron Eichler <319454444+aeichler-ac@users.noreply.github.com>

### [774679b](https://github.com/flashinfer-ai/flashinfer/commit/774679b4fc1a7ba9fb8bba6665fb3690eacad8ec)

- **作者**: lunarz-dev
- **时间**: 2026-09-09T17:56:17Z
- **提交信息**: fix(bench): quote benchmark CSV fields (#5045)

## 📌 Description

Replaces manual comma-joined benchmark CSV output with Python
csv.writer, so values containing commas—such as Unified MoE autotuner
tactics like (202, 469)—remain a single field. This prevents column
shifts that cause perf-ci to interpret dtype strings as Boolean values
during Databricks upload.

## 🔍 Related Issues

N/A — fixes the Unified MoE benchmark CSV ingestion regression observed
in perf-ci.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed pre-commit by running pip install pre-commit (or
used my preferred method).
- [x] I have installed the hooks with pre-commit install.
- [x] I have run the relevant hooks manually and fixed all reported
issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (unittest, etc.).


## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → Experimental APIs and Backends). Leave this section
untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
flashinfer/experimental/ and/or an @flashinfer_experimental_api.
Tracking issue: #

```experimental-tests
# Not an experimental PR.
```

## Reviewer Notes

The fix preserves the previous string conversion for all values; it only
delegates escaping and row serialization to the standard CSV writer.

### [75038cd](https://github.com/flashinfer-ai/flashinfer/commit/75038cdf67a5ba577ef4b329badc301f185c5a95)

- **作者**: RuQing Xu
- **时间**: 2026-09-09T17:48:58Z
- **提交信息**: perf(attention): Refresh DSL_FMHA cubins (#4997)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

+ Refresh DSL_FMHA cubins
+ Minimal change to source code to keep backward compatibility (unlike
cubin builder, FlashInfer needs to ensure JIT source compatibility with
multiple `nvidia-cutlass-dsl` versions).

### Performance on B300

Base shape: B=2, H=16, D=128 data:
- Internal compiler scheduling decision might have caused regression in
some shapes, but overall there is a consistent latency improvement over
the Blackwell Ultra horizon:

| S | Causal | QK/V | `main` median (ms) | Refresh median (ms) | Refresh
latency delta | Refresh speedup |

|---:|:------:|:------|-------------------:|--------------------:|----------------------:|----------------:|
| 2048 | True | BF16/BF16 | 0.064800 | 0.060704 | -6.32% | 1.0675x |
| 2048 | True | BF16/FP8 | 0.059040 | 0.055952 | -5.23% | 1.0552x |
| 2048 | True | FP8/FP8 | 0.053393 | 0.049728 | -6.86% | 1.0737x |
| 2048 | False | BF16/BF16 | 0.070321 | 0.065408 | -6.99% | 1.0751x |
| 2048 | False | BF16/FP8 | 0.061056 | 0.058912 | -3.51% | 1.0364x |
| 2048 | False | FP8/FP8 | 0.049504 | 0.049729 | +0.45% | 0.9955x |
| 16384 | True | BF16/BF16 | 1.386919 | 1.383943 | -0.21% | 1.0022x |
| 16384 | True | BF16/FP8 | 1.114918 | 1.170806 | +5.01% | 0.9523x |
| 16384 | True | FP8/FP8 | 1.050949 | 1.038149 | -1.22% | 1.0123x |
| 16384 | False | BF16/BF16 | 2.621342 | 2.425229 | -7.48% | 1.0809x |
| 16384 | False | BF16/FP8 | 2.146891 | 2.001659 | -6.76% | 1.0726x |
| 16384 | False | FP8/FP8 | 1.764121 | 1.729594 | -1.96% | 1.0200x |

## 🔍 Related Issues

<!-- Link any related issues here -->

N/A

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
## Summary by CodeRabbit

- **Bug Fixes**
- Updated the CuTe DSL fused multi-head attention backend for
compatibility with the latest kernel interface.
- Improved softmax-scaling behavior for skip-softmax and low-precision
attention modes.
- Added configurable rescaling thresholds for standard and block-scaled
attention paths.
- Refreshed backend artifacts and checksums across supported GPU and CPU
architectures.
- **Documentation**
- Clarified CuTe DSL attention backend coverage, including ALiBi and
modular prefill behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [10379bc](https://github.com/flashinfer-ai/flashinfer/commit/10379bc19827d92151f3c1c14081576a824a6b45)

- **作者**: Yuchen Wang
- **时间**: 2026-09-09T16:57:34Z
- **提交信息**: fix: apply calibration scales to ragged FP8 KV prefill (#4984)

<!-- .github/pull_request_template.md -->

## 📌 Description

Apply global `k_scale` / `v_scale` calibration in ragged FA2/FA3 prefill
with a 16-bit query and FP8 KV cache. Previously, the wrapper gated both
operations on the presence of NVFP4 block scale factors, silently
ignoring the documented calibration arguments for FP8 KV.

Fold K calibration into the softmax scale before logits soft capping,
and apply V calibration to the output without changing LSE. Leave the
existing NVFP4, full-FP8, and other backend paths unchanged.

Add a focused regression matrix checking outputs and base-2 LSE against
an FP32 reference over the actual quantized KV values. Thanks
@SamMausberg for the report and reproducer.

## 🔍 Related Issues

Fixes #4979. Related to #4977, which adds mixed-precision FA3 support
and explicitly leaves this wrapper issue separate; this PR does not
implement that FA3 kernel work.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Ran the official hooks on the changed files with `uvx pre-commit run
--files flashinfer/prefill.py tests/attention/test_fp8_prefill.py`; all
applicable hooks passed, including mypy and Ruff. The full-repository
hook run was not performed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

The checked result refers to the targeted tests below, not the entire
repository suite.

Validated on one B200 (SM100), using clean source-bound checkouts and
isolated source-JIT execution:

```sh
python -m pytest -q tests/attention/test_fp8_prefill.py::test_ragged_fp8_calibration_scales
```

- Candidate: **40 passed, 0 failed, 0 skipped**, exit 0. Covers
FP16/BF16 queries, e4m3/e5m2 KV, causal/noncausal attention,
omitted/unit/K-only/V-only/both scales, soft capping, finite output/LSE,
and caller-provided buffer aliasing.
- Test-only baseline: the first selected CUDA case fails the output
assertion (97.4% mismatched elements, max absolute error 0.495196), exit
1. This is a numerical failure, not an import or collection failure.
- Original reported shape: B=2, Q=KV=512, H=8, HKV=2, D=128, BF16
query/e4m3 KV, causal, no soft cap, K scale 0.25 and V scale 0.5: exit
0. Output max absolute error **0.000460476**, relative L2
**0.00280250**; LSE max absolute error **0.000430107**, relative L2
**0.0000116672**. All values finite; output/LSE buffers retain their
aliases.

The initial test reference incorrectly used natural-log LSE. It was
corrected to FlashInfer's base-2 convention, with no runtime-source or
tolerance changes. The earlier failed run is retained as a
test-reference error, not reported as passing. The baseline output
failure remains valid.

Validated commit: `2f253e0ba7111caf8d2d8ccf832f76678a2bb51a`. FA3/Hopper
execution and the full attention suite have not been validated locally.

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
backend is reachable on `backend="auto"` without
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

Please review the calibration boundary: 16-bit-query FP8-KV FA2/FA3 uses
the global scales here, while full-FP8 and other backends retain their
separate handling. Maintainer CI covering the other attention backends
would be appreciated.

Developed with Codex assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved FP8 prefill attention scaling across supported backends and
data types.
- Ensured key and value calibration scales are applied consistently,
including when scale factors are supplied through backend configuration.
- Improved numerical accuracy for FP8 attention outputs and log-sum-exp
results.

- **Tests**
- Added comprehensive coverage for FP8 calibration scales across data
types, execution modes, scaling combinations, and output configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4a23b40](https://github.com/flashinfer-ai/flashinfer/commit/4a23b40c1c3c518457260046de23a95ea78ff0f5)

- **作者**: IriKa
- **时间**: 2026-09-09T16:13:48Z
- **提交信息**: fix(decode): reserve max(K+V, st.o) smem for FA2 FP8+GQA decode (#5038)

The FA2 decode kernels (single + batch) placed smem_md (and the batch
kv_offset_smem) at a fixed offset assuming the K+V shared-memory buffer
is 2*num_stages_smem*bdy*tile_size_per_bdx*bdz*head_dim*sizeof(DTypeKV)
bytes. But sync_state (bdz > 1, i.e. GQA) reuses that buffer as float
storage for st.o, which needs bdz*bdy*head_dim*sizeof(float) bytes. When
FP8 (1-byte KV)
+ GQA (tile_size_per_bdx=1) + SM75 (num_stages_smem=1) all hold, the
float st.o is twice as large as the K+V buffer, so st.o overwrites
smem_md and runs past the allocation (illegal smem write -> crash).

Reserve max(K+V data, st.o float) for the K+V region in both the kernel
smem layout and the launcher smem_size. For every non-crashing config
the max() is a no-op (K+V >= st.o), so there is no behavior change.

Add tests/attention/test_decode_fp8_gqa.py covering FP8+GQA single/batch
decode against an fp16 reference.

#5030

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

## Summary by CodeRabbit

- **Bug Fixes**
- Fixed potential shared-memory overflow during FP8 grouped-query
attention decode operations.
- Improved reliability for single and paged batch decoding with FP8 KV
caches and grouped-query attention.

- **Tests**
- Added regression coverage for FP8 grouped-query attention in single-
and batch-decode workflows.
- Added validation across supported FP8 formats and paged KV-cache
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: IriKa Qiu <qiujie.jq@gmail.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [fb96128](https://github.com/flashinfer-ai/flashinfer/commit/fb9612816ade4cf93f5a48cd5605da1c7879ec0e)

- **作者**: feih-nv
- **时间**: 2026-09-09T10:25:55Z
- **提交信息**: feat(moe): split QuantConfig into weight/activation/output format axes (#4952)

<!-- .github/pull_request_template.md -->

## 📌 Description

### Why

`QuantVariant` mixed three kinds of names (formats like `NVFP4`, WxAy
labels like `W4A16`, kernel names like `Humming`), so it could not
express new MMA pairs:

- `W4A16` already means two weight encodings: MXFP4 on TRTLLM / CUTLASS
SM90, NVFP4 on CuTe-DSL / b12x. With several candidates, the autotuner's
pick decided the weight format.
- `MXFP4` means MXFP4×MXFP8 (W4A8), and MXFP4×MXFP4 was inexpressible.
- `MxInt4` is MXINT4 weights × BF16 activations, a third W4A16-style
encoding the name did not show.

### Design

```python
class QuantFormat(Enum):
    BF16, FP16, FP8PerTensor, DeepSeekFp8, MXFP8, NVFP4, MXFP4, MXINT4, INT4

@dataclass(frozen=True)
class QuantConfig:
    weight: QuantFormat                          # MMA weight operand
    activation: QuantFormat                      # MMA activation operand
    output: QuantFormat = QuantFormat.BF16       # layer output
    variant: Optional[QuantVariant]              # derived from the pair (init=False); constructor accepts variant= as a deprecated preset
    swizzled_scale_factors / per_token_scale     # unchanged

    # an omitted axis is BF16 (unquantized); knobs after the three axes are keyword-only
```

Axes are the MMA numeric formats, not the dtype crossing the Python API:
CUTLASS NVFP4 takes BF16 activations and quantizes in-kernel, and is
still `(NVFP4, NVFP4)`.

Runners declare `supported_quant_variants` and
`supported_output_formats` separately because output does not vary by
pair today (every runner is BF16-only; `FP16` is in the enum for later).
`MoELayer` filters candidates on both before build.

### API

- New `QuantFormat` enum, exported from `flashinfer.fused_moe`. `FP16`
and `INT4` are new names; `MXFP8` / `MXINT4` replace the `MxFp8` /
`MxInt4` spellings.
- `QuantConfig(weight, activation, output)`: an omitted axis is BF16,
i.e. unquantized (`QuantConfig()` is BF16×BF16;
`QuantConfig(weight=MXFP4)` is MXFP4 weights with BF16 activations,
W4A16; MXFP4×MXFP8 needs both axes). The three axes are positional,
everything after them keyword-only. `QuantConfig` is structural only;
legal combinations are runner capabilities.
- `QuantVariant` stays as a deprecated preset:
`QuantConfig(variant=NVFP4)` expands to the pair and emits a
`DeprecationWarning`. The stored `variant` is derived from the pair and
excluded from `__init__` fields, so `dataclasses.replace` re-derives it
instead of replaying it.
- `QuantVariant.W4A16` is rejected as `variant=`; spell the pair
(`QuantConfig(MXFP4, BF16)` / `QuantConfig(NVFP4, BF16)`) or use
`QuantConfig.from_variant(W4A16, w4a16_weight=...)`, which also warns.

### Runners and layer

- `supported_quant_variants` now holds `(weight, activation)` pairs (a
variant is one such combination) plus `supported_output_formats`;
`supported_activation_classes_by_quant` is keyed by pair.
- Pairs without a `QuantVariant` mapping are rejected by
`check_support()` for now: runner build paths and weight preparation
still dispatch on `QuantVariant`, so such a pair would pass capability
checks and fail later. Lifted when dispatch keys on `quant.pair`
(config-merge follow-up).
- `_cache_key_extras` uses the three format names instead of
`variant.name`; persisted autotune cache keys invalidate once.

### Consumers

- moe_ep split kernel: `build_activation_pack` and siblings take `quant:
QuantConfig` instead of `quant_variant: QuantVariant`; `mxfp8_dispatch`
validates `(MXFP4, MXFP8)`; weight materialization dispatches on the
pair.
- `benchmarks/bench_cute_dsl_moe_distributed.py` builds the pair
explicitly.
- `scripts/generate_moe_activation_matrix.py` labels rows
`weight×activation` (matrix regenerated). Design doc §2 / §3 updated and
a "QuantConfig three-axis formats" section added.
`docs/api/fused_moe.rst` gains a "Unified MoE API" autosummary
(`MoELayer`, config types incl. `QuantFormat`, packs), which were not
listed before.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

New CPU tests:

- `QuantConfig` construction: both-or-neither axes, `variant=` expansion
and conflicts, `dataclasses.replace`, repr round-trip.
- Runner and `MoELayer` gating on `(weight, activation)` pairs and
`output`, including the error text.
- Pair-keyed `supported_activation_classes_by_quant` and the
activation-matrix generator.

Updated: unified-MoE, EP bridge, and activation-matrix tests construct
configs from pairs. No GPU tests added; kernel paths are unchanged.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added explicit weight, activation, and output quantization formats to
the unified MoE API.
  * Added backend support checks for format pairs and output formats.
  * Exposed `QuantFormat` through the public fused MoE API.
  * Defaulted unspecified quantization axes to BF16.
* Retained legacy presets with deprecation warnings and conversion
support.

* **Documentation**
* Updated API and design documentation with the new configuration model
and examples.

* **Bug Fixes**
* Improved unsupported-configuration errors to identify configured
quantization formats.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8e3854b](https://github.com/flashinfer-ai/flashinfer/commit/8e3854bcec6e257cdfc674e579cff64018b86e63)

- **作者**: eigen
- **时间**: 2026-09-09T09:12:23Z
- **提交信息**: feat(cake_gqa): Add an experimental SM110 GQA decode kernel (#5052)

## 📌 Description

Add an explicit experimental FP16 decode API for NVIDIA SM110. The
initial
specialization targets one decode token with 32 query heads, 8 key/value
heads,
head dimension 128, dense stacked KV storage, and independent
valid-prefix
lengths per request.

The implementation includes:

- a thin `flashinfer.sm110_gqa_decode` entry point;
- pre-launch rejection of sequence lengths outside inclusive `[1,
capacity]`;
- exact-SM110 JIT loading with per-source SHA-256 verification;
- separate 256-thread short-prefix and 384-thread pipelined long-prefix
CUDA
  kernels;
- source-package data, four-shape correctness tests, a runnable example,
and a
  reproducible cold-L2 CUPTI benchmark.

### Primary performance baseline: XQA

Fresh paired measurements on 2026-09-09 compare the actual exported
kernels
at `105a1efd2bae8a0ab8ab3a0895f2114a019b5754` against a fixed
ahead-of-time
XQA specialization. NVIDIA Thor / SM110, CUDA 13.5, FP16,
Hq32/Hkv8/D128,
one query token, same-process identical inputs, cold-L2 CUPTI median GPU
activity spans:

| Shape | Valid lengths | Exported SM110 kernel | XQA | Speedup vs. XQA
|
| --- | --- | ---: | ---: | ---: |
| B1, capacity 64 | `[1]` | 0.004512 ms | 0.005792 ms | 1.284x |
| B4, capacity 256 | `[64, 127, 191, 256]` | 0.026048 ms | 0.032768 ms |
1.258x |
| B1, capacity 1024 | `[1024]` | 0.035745 ms | 0.041984 ms | 1.175x |
| B1, capacity 4096 | `[3968]` | 0.117633 ms | 0.124513 ms | 1.058x |

All four medians beat XQA. Both arms reuse separate preallocated outputs
and launch exactly one prepared kernel per sample. Compilation, view
preparation, output allocation, and public API sequence-length
validation
are excluded. These are **kernel-only** results, not public API latency.
All four shapes ran in one process with three counterbalanced groups,
100 ms warmup and 1000 ms target measurement duration per arm, a 6x
duration
safety factor, and required CUPTI with a per-sample L2 flush. Device
clocks
were not locked. Every sample was checked for one launch and one
expected
kernel activity.

The XQA artifact is loaded directly, not through the public XQA
dispatcher.
The paired driver and XQA artifact are not bundled in this PR. Full
protocol,
input seeds, artifact identities, and the supplementary comparison are
in

[`RESULTS.md`](https://github.com/yyihuang/flashinfer/blob/feat/sm110-gqa-decode/flashinfer/experimental/sm110_gqa_decode/RESULTS.md).

### Supplementary public API comparison: PyTorch SDPA

Both timed calls allocate and return their output tensor; neither reuses
a
caller-provided output buffer.
The candidate measurement includes the public API's sequence-length
validation.
This separate same-process cold-L2 CUPTI comparison on NVIDIA Thor /
CUDA 13.5
does not replace XQA as the kernel-performance baseline.

| Shape | Valid lengths | SM110 GQA decode | PyTorch SDPA | Speedup |
| --- | --- | ---: | ---: | ---: |
| B1, capacity 64 | `[1]` | 0.161282 ms | 0.541734 ms | 3.36x |
| B4, capacity 256 | `[64, 127, 191, 256]` | 0.184097 ms | 0.632294 ms |
3.43x |
| B1, capacity 1024 | `[1024]` | 0.193154 ms | 0.629159 ms | 3.26x |
| B1, capacity 4096 | `[3968]` | 0.277633 ms | 2.361688 ms | 8.51x |

## 🔍 Related Issues

Tracks #5051.

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated on NVIDIA Thor / SM110 with CUDA 13.5:

- targeted API and invalid-input tests — 6 passed
- exact-SM110 four-shape correctness — 4 passed
- `python benchmarks/bench_sm110_gqa_decode.py` — all four rows
completed
- fresh paired XQA measurement — all four rows completed in one process;
public API, prepared exported kernel, and XQA passed the independent
FP32
  oracle at `atol=rtol=1e-2`, with finite outputs and unchanged inputs

Retained sanitizer evidence on NVIDIA Thor / SM110 with CUDA 13.4
(kernel
sources and launch configuration are unchanged):

- Compute Sanitizer `synccheck` — 0 errors
- Compute Sanitizer `racecheck` — 0 hazards, 0 errors, 0 warnings

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #5051
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
tests/experimental/test_sm110_gqa_decode.py
```

## Reviewer Notes

The API name intentionally omits the fixed group ratio. The experimental
backend and documentation make the current 4:1 Hq32/Hkv8 geometry
explicit so
the public name can survive future shape expansion.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added experimental FP16 grouped-query attention decode support for
NVIDIA SM110 GPUs.
  - Added a public API with optional output storage and query scaling.
- Added usage examples, performance benchmarking, and optional JSON
output.
- Added documentation covering supported hardware and input
requirements.

- **Validation**
- Added checks for tensor compatibility and sequence lengths within the
supported range.

- **Tests**
- Added correctness, route-selection, manifest, and input-preservation
tests.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4363
- **最后更新**: 2026-09-09T10:25:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34477
- **最后更新**: 2026-09-09T22:06:01Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: YiYi Xu, Shreshth Saini

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **功能新增**：新增社区脚本（CachedSearch），用于视频生成管线的测试时搜索优化
- **文档更新**：完善 agent 开发指南和贡献指南，明确 PR 沟通规范

### 2. 关键变更点与项目方向的关系
- **CachedSearch 脚本**：这是社区贡献的测试时搜索工具，核心思路是在 FirstBlockCache 下运行所有候选，仅对胜出种子进行全计算再生。这与 diffusers 项目“模块化、可扩展”的核心理念一致——通过社区脚本形式提供实验性功能，不侵入核心代码库，同时为视频生成场景提供更高效的推理方案。
- **文档规范更新**：强调 helper 函数必须使用显式参数而非 `components`，并明确 human-in-the-loop 规则限于沟通层面，要求 PR 沟通简洁且人类可读。这反映了项目在 AI 辅助开发（Claude 参与）背景下，对代码可维护性和协作流程的重视。

### 3. 对项目的影响和潜在意义
- CachedSearch 为视频生成推理提供了“低成本试错”方案，可能吸引更多研究者和开发者尝试多候选搜索策略，推动视频生成质量提升。
- 文档更新虽不改变功能，但能降低社区贡献门槛，规范 AI 辅助生成的代码质量，长期看有助于维护项目健康度。

### 4. 值得关注的技术点
- **FirstBlockCache 机制**：这是一种缓存策略，让多个候选共享首块计算结果，大幅降低测试时搜索的计算开销，值得关注其实现细节和适用边界。
- **显式参数 vs `components`**：这一约定有助于减少隐式依赖，提升代码可读性和可测试性，对大型库的长期演进尤为重要。

### 5. 对项目发展的影响
diffusers 作为 HuggingFace 生态的核心生成模型库，持续通过社区脚本吸收前沿研究（如本次的缓存搜索），同时通过文档规范强化协作质量。这两个提交分别从“技术能力扩展”和“社区治理”两个维度支撑项目规模化发展——前者保持技术领先性，后者确保在 AI 辅助编码普及的背景下，代码质量和沟通效率不失控。整体上，项目正朝着“更高效推理 + 更规范协作”的方向稳步前进。

## 详细提交记录

### [3c22124](https://github.com/huggingface/diffusers/commit/3c22124636a332a0df02910f609315d4c2898f57)

- **作者**: Shreshth Saini
- **时间**: 2026-09-09T18:37:09Z
- **提交信息**: [Community] Add CachedSearch script: cheaper best-of-N for video pipelines (#14735)

Test-time search where every candidate runs under FirstBlockCache and only
the winning seed is regenerated at full compute.
Paper: https://huggingface.co/papers/2607.23159

### [ebe93ee](https://github.com/huggingface/diffusers/commit/ebe93ee5f761455ca99301b902f373fd00fb996d)

- **作者**: YiYi Xu
- **时间**: 2026-09-09T18:32:53Z
- **提交信息**: agent doc: add a requirement for PR communications (#14709)

* modular guide: helpers take explicit arguments, not `components`

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* agent guide: human-in-the-loop rules, helpers take explicit arguments

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* clarify human-in-the-loop scope to communication

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* contribution guide + agent guide: PR communication must be concise and human-readable

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HCdbvRpL9fv3h3WwSUPpfS

* Apply batched suggestions from code review

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Apply suggestion from @yiyixuxu

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-08-31T08:28:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13078
- **最后更新**: 2026-09-09T19:09:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35715
- **最后更新**: 2026-09-10T00:02:29Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 20
- **主要提交者**: Elizaveta Martirosian, Mohammad Miadh Angkad, Zhiqiang Xie

## AI分析总结

# SGLang 仓库提交分析总结

## 一、主要更新类型

本次提交涵盖多种类型，包括：**CI/CD改进**（多条）、**Bug修复**（多条）、**性能优化**（多条）、**新模型支持**（多条）、**硬件适配**（NPU/AMD/XPU）、**架构重构**及**功能回退**。

## 二、关键变更点与项目方向

1. **CI/CD体系强化**：新增`/run-full-ci`和`/run-extra-ci`斜杠命令，将AMD ROCm 10设为默认测试环境，合并XPU CI阶段并调整包范围。这些改进直接服务于项目“多硬件平台支持”的核心目标，降低测试门槛、提升回归检测效率。

2. **多硬件生态扩展**：NPU方向优化LTX-2/2.3推理性能、设置DeepEP混合部署参数、升级memfabric和sgl-kernel-npu版本；XPU方向修复夜间构建阻塞；AMD方向统一ROCm 10测试基线。这些提交表明项目正加速构建跨NPU/XPU/AMD的完整推理栈。

3. **新模型与格式支持**：新增GLM-5.3 Flash NVFP4加载支持、SenseNova-U1.5-8B-MoT模型、Kimi-K3的fp32路由权重兼容，以及GLM-5.2 DSA-MTP变体的GSM8K阈值调整。这延续了项目“快速跟进前沿模型”的策略，保持与最新开源模型生态同步。

4. **推理架构深度优化**：Rust服务端将DP注意力改为节点本地HTTP端口，规避跨节点通信瓶颈；为DP gather场景保留共享MAX_LEN prefill CUDA图桶以修复MegaMoE稀疏DP挂起；FlashInfer MLA的indptr缓冲区按填充后最大批次分配。这些改动直接提升大规模分布式推理的稳定性和吞吐。

5. **内存与缓存机制改进**：HiCache以分段锁协议替代skip_lock_node_ids，降低锁竞争；Mamba前缀缓存按配置的SSM状态dtype存储检查点；统一内存层修复Mamba字节短缺时的Full KV驱逐问题。这些优化强化了项目在长序列和混合架构场景下的内存效率。

## 三、项目影响与潜在意义

- **稳定性提升**：多项针对DP注意力、CUDA图捕获、序列并行状态标记的修复，直接解决生产环境中的挂起和内存泄漏问题，增强系统可靠性。
- **多硬件战略加速**：NPU/XPU/AMD的密集投入表明项目正从“GPU优先”转向“全硬件覆盖”，扩大潜在用户群。
- **新模型快速集成**：对GLM、SenseNova等最新模型的及时支持，巩固了SGLang作为“高性能推理框架首选”的定位。

## 四、值得关注的技术点

- **DP注意力节点本地端口方案**：通过避免跨节点共享端口来降低延迟，是分布式推理通信层的重要优化。
- **分段锁协议替代节点跳过**：更细粒度的锁控制有望在高并发缓存访问下显著提升吞吐。
- **CUDA图桶的DP gather兼容处理**：解决稀疏DP场景下的图捕获冲突，属于推理引擎底层调优。
- **Mamba状态dtype一致性**：确保前缀缓存与计算精度匹配，避免精度损失或转换开销。

## 五、对项目发展的整体影响

结合README中SGLang“高性能、低延迟推理服务”的定位，这些提交从三个维度推动项目演进：**一是工程化成熟度**，通过CI自动化和多硬件测试矩阵，为大规模部署提供质量保障；**二是架构前瞻性**，在DP注意力、内存管理、缓存协议等核心组件上的深度优化，为未来更大规模模型和更长上下文场景奠定基础；**三是生态覆盖广度**，持续跟进新模型和硬件平台，保持框架在快速迭代的AI领域的竞争力。整体来看，项目正处于从“功能完善”向“全场景生产就绪”过渡的关键阶段。

## 详细提交记录

### [2092f6d](https://github.com/sgl-project/sglang/commit/2092f6df05960c52d9df1994b0af812c2fc6544a)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-09T23:00:17Z
- **提交信息**: [CI] Install helion 1.4.0 for the KDA Helion kernel tests (#38688)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>
Co-authored-by: Alison Shao <54658187+alisonshao@users.noreply.github.com>

### [51c8581](https://github.com/sgl-project/sglang/commit/51c8581a26b277fae13fdd924b4b484d0e2dc1ba)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-09-09T22:55:13Z
- **提交信息**: [Rust] Gate health on startup warmup completion (#37994)

### [beaf3d9](https://github.com/sgl-project/sglang/commit/beaf3d92522ea059f827bee716326b20f2ae5135)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-09T21:55:51Z
- **提交信息**: [HiCache] Replace skip_lock_node_ids with a segment lock protocol (#36848)

### [a84ffd1](https://github.com/sgl-project/sglang/commit/a84ffd13260b2a43fbe13b0c044ff725aa6a9f58)

- **作者**: Francis
- **时间**: 2026-09-09T21:12:15Z
- **提交信息**: feat: add optimized Domino rollout to DFlash V2 (#36899)

Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [2948a62](https://github.com/sgl-project/sglang/commit/2948a62a6f5527468e7b9a22b9fd9da22a024eaf)

- **作者**: Alison Shao
- **时间**: 2026-09-09T20:56:38Z
- **提交信息**: [CI] Add /run-full-ci and /run-extra-ci slash commands (#38734)

### [96d91ef](https://github.com/sgl-project/sglang/commit/96d91ef9266d2bebd8e8c09ef1f28b2d521631ff)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-09-09T20:51:08Z
- **提交信息**: [Model] Support GLM-5.3 Flash NVFP4 loading (#38621)

Co-authored-by: YAMY <74099316+YAMY1234@users.noreply.github.com>

### [bede776](https://github.com/sgl-project/sglang/commit/bede776c2af38d6fb84d6fa365bba8cc033af6fd)

- **作者**: SuperSong
- **时间**: 2026-09-09T20:46:51Z
- **提交信息**: fix(unified-memory): evict Full KV for Mamba byte shortfalls (#36713)

Co-authored-by: Yangmin Li <yangminl@nvidia.com>
Co-authored-by: YAMY <74099316+YAMY1234@users.noreply.github.com>

### [6c1d0b1](https://github.com/sgl-project/sglang/commit/6c1d0b1b2987bfe3a620dc2f330ba4507d355488)

- **作者**: paulzhang-tm
- **时间**: 2026-09-09T20:01:16Z
- **提交信息**: Revert "[Spec] Publish the final multi-layer EAGLE shared-read event" (#38041)

### [95a88bf](https://github.com/sgl-project/sglang/commit/95a88bfd69d32ca46173f4abdec312cff8ab12bb)

- **作者**: Alison Shao
- **时间**: 2026-09-09T19:46:10Z
- **提交信息**: Relax GSM8K thresholds for the GLM-5.2 DSA-MTP variants (#38725)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [354ee46](https://github.com/sgl-project/sglang/commit/354ee46c26b4c0c63760234a10c57c9498c45199)

- **作者**: cctry
- **时间**: 2026-09-09T18:56:30Z
- **提交信息**: Keep VMM capability votes on CPU (#38722)

### [8733da8](https://github.com/sgl-project/sglang/commit/8733da8cf46089a1fc7d86b36eb5f6ba62ea89c5)

- **作者**: Sage
- **时间**: 2026-09-09T18:22:44Z
- **提交信息**: [rust-server] Use node-local HTTP ports for DP attention (#34430)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [7b791c9](https://github.com/sgl-project/sglang/commit/7b791c9534ad4a834bd16827b91a7c09b3260557)

- **作者**: YAMY
- **时间**: 2026-09-09T17:52:16Z
- **提交信息**: [Bugfix] Keep a shared MAX_LEN prefill CUDA graph bucket when the graph captures a DP gather (MegaMoE sparse-DP hang) (#37933)

Co-authored-by: shyeh25 <206795756+shyeh25@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [0027af2](https://github.com/sgl-project/sglang/commit/0027af2eace5ccc2116c8c993ce71aebf1535264)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-09-09T16:36:18Z
- **提交信息**: [diffusion] [NPU] Optimize LTX-2/2.3 inference performance for NPU (#34722)

Co-authored-by: Elizaveta Martirosian <you@example.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>
Co-authored-by: root <root@localhost.localdomain>
Co-authored-by: Makcum888e <79456407+Makcum888e@users.noreply.github.com>
Co-authored-by: mickqian <mickqian@users.noreply.github.com>

### [2b1c4e4](https://github.com/sgl-project/sglang/commit/2b1c4e4c854ae41916f7df22b49931c83b97d984)

- **作者**: pllimax
- **时间**: 2026-09-09T16:08:07Z
- **提交信息**: [NPU] Set DEEPEP_HYBRID_DEPLOYMENT=1 for collocated DeepEP test cases (#38667)

### [ffe98a4](https://github.com/sgl-project/sglang/commit/ffe98a4279ba6e42d1f87dc4eeb6edb4887b9ea4)

- **作者**: HuangJi
- **时间**: 2026-09-09T12:00:03Z
- **提交信息**: [Diffusion][MiniMax-H3] Add SM90 Sage compute for SubBlock sparse attention (#37982)

### [dba34cc](https://github.com/sgl-project/sglang/commit/dba34cc96457895f8441619f255b17f28fd749d3)

- **作者**: Even Zhou
- **时间**: 2026-09-09T11:53:49Z
- **提交信息**: [NPU] Bump memfabric and sgl-kernel-npu versions in docs and pyproject_npu.toml (#38437)

### [708f51e](https://github.com/sgl-project/sglang/commit/708f51e44bc64f546a60fa9631f0e7d99493d0a0)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-09-09T09:28:20Z
- **提交信息**: [AMD][CI] Make ROCm 10 the Default for AMD PR and Nightly Tests (#38659)

Co-authored-by: Chen Bingxu <bingxche@amd.com>

### [72d5c5b](https://github.com/sgl-project/sglang/commit/72d5c5bb73cadd7ffbf5114e5f81e29d36b6c61a)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-09T08:33:39Z
- **提交信息**: [Kimi-K3] Accept fp32 routing weights in the fused MoE finalize (#38612)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [d10ebdd](https://github.com/sgl-project/sglang/commit/d10ebdd0cb40887376811098bc9a4714a59c64d0)

- **作者**: ashwini rathi
- **时间**: 2026-09-09T08:32:16Z
- **提交信息**: docker(xpu): unblock nightly build (setvars.sh + sgl-kernel rename) (#38617)

Co-authored-by: arathi-hlab <arathi-hlab@users.noreply.github.com>

### [07c7b26](https://github.com/sgl-project/sglang/commit/07c7b2674d4321d6ca4e7db1fb0f78779250b2b9)

- **作者**: ashwini rathi
- **时间**: 2026-09-09T08:26:54Z
- **提交信息**: ci(xpu): merge stage-a+b into one job and trim main_package scope (#38014)

Co-authored-by: arathi-hlab <arathi-hlab@users.noreply.github.com>

### [1ad3eb0](https://github.com/sgl-project/sglang/commit/1ad3eb09a91f7389a087716dbe82ddb4b3e25d20)

- **作者**: YAMY
- **时间**: 2026-09-09T08:25:29Z
- **提交信息**: [Attention] Size FlashInfer MLA indptr buffers to the padded max batch (#38590)

### [32d7d94](https://github.com/sgl-project/sglang/commit/32d7d943d1149f30b40b021c3a339cdcba1bb6a9)

- **作者**: MingxuZh
- **时间**: 2026-09-09T08:21:24Z
- **提交信息**: use private --shm-size instead of --ipc=host to stop /dev/shm leak (#38638)

### [35df2fe](https://github.com/sgl-project/sglang/commit/35df2fecde7acec19c59d3fa1186ffc49f02deb6)

- **作者**: Pranjal Shankhdhar
- **时间**: 2026-09-09T08:03:03Z
- **提交信息**: [Fix] Stamp sequence-parallel state on dummy forward batches (#38564)

Co-authored-by: pranjalssh <pranjalssh@fb.com>

### [13469c1](https://github.com/sgl-project/sglang/commit/13469c16d3e9f857c53c3f33da8d33268fd4f570)

- **作者**: Yuhao Yang
- **时间**: 2026-09-09T07:25:57Z
- **提交信息**: Store mamba prefix-cache checkpoints at the configured SSM state dtype (#34820)

### [daf66f6](https://github.com/sgl-project/sglang/commit/daf66f6670724b27e07f26b99514517d82e1a89f)

- **作者**: Yuefeng Wu
- **时间**: 2026-09-09T07:12:38Z
- **提交信息**: [Diffusion][SenseNova] support SenseNova-U1.5-8B-MoT  (#36606)

Co-authored-by: wuyuefeng <wuyuefeng@noreply.gitcode.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1276
- **最后更新**: 2026-09-09T08:56:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91367
- **最后更新**: 2026-09-10T00:01:10Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 32
- **主要提交者**: abrahamzewoudie, Jefrey Cayab, Aarushi Jain

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型分布

本次共37个提交，按类型划分：**Bug修复**约12个（占比最高），**ROCm/AMD平台适配与优化**约10个，**性能优化**约4个，**CI/测试改进**约4个，**功能新增**约3个，**文档与重构**各2个。

## 二、关键变更点与项目方向的关系

**1. ROCm/AMD生态持续强化**：多个提交围绕AITER内核集成（索引器评分、top-k内核、FP8 KV测试容差调整）、MI300分布式编译拆分、共享KV prefill支持等，体现vLLM对AMD硬件生态的深度投入，与“为所有人提供LLM服务”的目标一致。

**2. 模型架构演进**：统一XD-RoPE到M-RoPE并推导通道数、为Kimi-K3添加流水线并行支持、Qwen4Exp支持UVA PLE-offload和Engram张量并行、Gemma4启用QKV-Fuser，显示vLLM正快速适配最新模型架构。

**3. 解析器与结构化输出修复**：Seed-OSS轮次边界token、Step-3.5推理解析器、无效结构化输出请求不再停止引擎等修复，提升推理服务的鲁棒性和可用性。

**4. 前端与API完善**：Rust前端跳过未定义token id、使--max-model-len可选、拒绝不支持的Responses API输入并返回400错误，改善开发者体验。

## 三、对项目的影响与潜在意义

- **稳定性提升**：多项Bugfix（如FlexAttention重编译、DP token padding排除、record_stream索引映射）直接改善生产环境的可靠性。
- **性能优化**：TRTLLM ragged prefill性能回退修复、BF16x3路由GEMM精度提升并默认启用、NVFP4 DSpark top-k投影等，持续推动推理吞吐和延迟优化。
- **可观测性增强**：LoRA适配器无权重时记录日志、pooling响应中报告LoRA适配器名称，便于用户排查问题。

## 四、值得关注的技术点

1. **AITER内核深度集成**：AMD平台将索引器评分和top-k内核集成到MiniMax-M3稀疏注意力路径，是稀疏注意力优化的前沿方向。
2. **PP draft broadcast的record_stream修复**：涉及流水线并行下的显存管理，对长序列推理稳定性至关重要。
3. **KV offload重构（block→chunk）**：术语统一暗示KV缓存卸载逻辑的架构梳理，为后续功能扩展铺路。
4. **EC连接器端到端测试**：新增scale-out EC连接器流程测试，强化分布式扩展能力验证。

## 五、对项目发展的整体影响

结合README中“Easy, fast, and cheap LLM serving for everyone”的定位，这些提交体现了vLLM在三个维度的持续演进：**硬件覆盖广度**（AMD ROCm、NVIDIA新架构sm100）、**模型适配速度**（紧跟最新开源模型如Qwen4Exp、Gemma4、Kimi-K3）、**服务稳定性深度**（解析器、结构化输出、显存管理等多层修复）。值得注意的是，多个提交由AMD、IBM、Intel等公司工程师贡献，显示vLLM已形成跨厂商协作的开源生态。AI辅助编码工具（Claude、Cursor、Codex）在Co-author中出现频率较高，反映AI辅助开发已成为主流工作流。整体来看，vLLM正从“高性能推理引擎”向“全栈、多硬件、生产就绪的LLM服务平台”演进。

## 详细提交记录

### [65f3fca](https://github.com/vllm-project/vllm/commit/65f3fca5683b4c7d48906ff8b2fd44903ec5dba6)

- **作者**: Mikhail Podvitskii
- **时间**: 2026-09-09T23:29:30Z
- **提交信息**: [Bugfix][Parser] Seed-OSS turn-boundary tokens + boundary-fallback tests (#54264)

Signed-off-by: Mikhail Podvitskii <podvitskiymichael@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [4ebf61e](https://github.com/vllm-project/vllm/commit/4ebf61ebda8dc8bf090bd4ee14d2855f694111b0)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-09T22:57:01Z
- **提交信息**: [Cohere] Bound remaining request priorities to the MessagePack int64 range (#56146)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [83252ea](https://github.com/vllm-project/vllm/commit/83252ea899c6538eaa0c1fb31f28a92c661bbffc)

- **作者**: ykamiset
- **时间**: 2026-09-09T22:40:33Z
- **提交信息**: [Performance][ROCm]  Integrate aiter indexer scoring and top-k kernels into MiniMax-M3 sparse attention path (#52664)

Signed-off-by: Yamini Preethi Kamisetty <YaminiPreethi.Kamisetty@amd.com>

### [6983a08](https://github.com/vllm-project/vllm/commit/6983a0883dc831d33ffa2713b955159894a350d7)

- **作者**: Aarushi Jain
- **时间**: 2026-09-09T22:07:51Z
- **提交信息**: [ROCm][CI] Split MI300 Distributed Compile by graph partition mode (#53602)

Signed-off-by: Aarushi Jain <142941703+aarushjain29@users.noreply.github.com>
Signed-off-by: Aarushi Jain <aarushi.jain2@amd.com>

### [dcd5444](https://github.com/vllm-project/vllm/commit/dcd544486b7f4672b3c2e60ea289f19d86cf355c)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-09T21:51:34Z
- **提交信息**: [ROCm][Bugfix] Support shared KV prefill in AITER attention (#55887)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [26fec6d](https://github.com/vllm-project/vllm/commit/26fec6d183c3957ee4dc0022452c430e745dd20f)

- **作者**: yzong-rh
- **时间**: 2026-09-09T21:10:23Z
- **提交信息**: [Bugfix] Fix Step-3.5 reasoning parser for structured outputs (#53174)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [8c87c33](https://github.com/vllm-project/vllm/commit/8c87c333b84c85908b1d11f0044457692277c6f3)

- **作者**: Wei Zhao
- **时间**: 2026-09-09T20:38:20Z
- **提交信息**: [Perf] Fix TRTLLM ragged prefill perf regression (#55499)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [56d001f](https://github.com/vllm-project/vllm/commit/56d001faf0f53c72fcedbbdd77e5418f68fe7494)

- **作者**: wuhangxian
- **时间**: 2026-09-09T20:10:28Z
- **提交信息**: [Bugfix] Detect OpenAI content format when message.content is passed through macro parameters (#53824)

Signed-off-by: wuhangxian <1391938827@qq.com>
Signed-off-by: wuhangxian <wuhangxian@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: wuhangxian <wuhangxian@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [cce5065](https://github.com/vllm-project/vllm/commit/cce50657b742598a5b8874fc9fe3a94dc4344a14)

- **作者**: djramic
- **时间**: 2026-09-09T20:08:39Z
- **提交信息**: [ROCm][CI] Use a platform-independent GEMM in the merged-column fuser test (#56130)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [e8064a9](https://github.com/vllm-project/vllm/commit/e8064a96d02db70ebc1ca922bc9aba967a654483)

- **作者**: Chris Eastwood
- **时间**: 2026-09-09T19:55:56Z
- **提交信息**: [Bugfix][V2] record_stream idx_mapping in the PP draft broadcast (#55745)

Signed-off-by: Chris Eastwood <chris.eastwood@pwn4g3.dev>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [c69d5d7](https://github.com/vllm-project/vllm/commit/c69d5d72a6018db6ff55efc66097d377c25828cc)

- **作者**: Aarushi Jain
- **时间**: 2026-09-09T18:10:26Z
- **提交信息**: [CI][ROCm] Increase timeout for AMD MI355 Language Models (Standard) (#56114)

Signed-off-by: Aarushi Jain <aarushi.jain2@amd.com>

### [3fb676b](https://github.com/vllm-project/vllm/commit/3fb676bfad0f1c7099af6296983e739be3fe29cc)

- **作者**: Divakar Verma
- **时间**: 2026-09-09T17:48:14Z
- **提交信息**: [ROCm][CI] Fix moe layer tests for fp8 dtype compatibility (#56106)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [a207d7c](https://github.com/vllm-project/vllm/commit/a207d7ce1d0cc33121726a7189080a0fa40ebb4d)

- **作者**: Guancheng Fu
- **时间**: 2026-09-09T17:44:46Z
- **提交信息**: [Bugfix][LoRA] Log when an adapter applies no weights (#55310)

Signed-off-by: Guancheng Fu <110874468+gc-fu@users.noreply.github.com>

### [22d95d1](https://github.com/vllm-project/vllm/commit/22d95d1adc24d5834ec45bb697170a76cf4c9a95)

- **作者**: cjackal
- **时间**: 2026-09-09T17:43:22Z
- **提交信息**: [Bugfix] Make `mm_device_do_normalize` encoder-cudagraph safe (#55370)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [83fe993](https://github.com/vllm-project/vllm/commit/83fe99399ec0603b32393a14324b65c67ad04af2)

- **作者**: Andrii Skliar
- **时间**: 2026-09-09T17:33:46Z
- **提交信息**: [Spec Decode] Add NVFP4 DSpark gathered top-k projection (#55713)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [af51d0e](https://github.com/vllm-project/vllm/commit/af51d0ef03ecf62302b51e7ab3042b088449d6b5)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-09T17:31:13Z
- **提交信息**: [Pooling] Report LoRA adapter names in responses (#56004)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [1454b71](https://github.com/vllm-project/vllm/commit/1454b7172796c00955ae32e3fe865b98b262855a)

- **作者**: Aarushi Jain
- **时间**: 2026-09-09T17:22:25Z
- **提交信息**: Fix ROCm AITER FP8 KV test tolerances. (#53590)

Signed-off-by: Aarushi Jain <aarushjain29@users.noreply.github.com>
Co-authored-by: Aarushi Jain <aarushjain29@users.noreply.github.com>

### [42d76ee](https://github.com/vllm-project/vllm/commit/42d76ee35a2ad2352fa4f58e2781ea607d0c39bd)

- **作者**: Harry Mellor
- **时间**: 2026-09-09T17:11:40Z
- **提交信息**: [Docs] Fix griffe docstring indentation warning in `SupportsMRoPE` (#56112)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [719284f](https://github.com/vllm-project/vllm/commit/719284fe158f1be8a9dd92953295fc9d49015730)

- **作者**: Harry Mellor
- **时间**: 2026-09-09T16:23:30Z
- **提交信息**: [Core][Model] Unify XD-RoPE into M-RoPE and derive the channel count (#56078)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [c55e15a](https://github.com/vllm-project/vllm/commit/c55e15a44ec4127832d4a86928a356fdd9e68dbd)

- **作者**: Clinton Thomas
- **时间**: 2026-09-09T15:32:01Z
- **提交信息**: [Structured Output] Keep invalid structured-output requests from stopping the engine (#51450)

Co-authored-by: Lucas Bourtoule <35483370+dhalf@users.noreply.github.com>
Co-authored-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>

### [7e95735](https://github.com/vllm-project/vllm/commit/7e95735eb90fd6497a9386f515db4242688a9abb)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-09T15:10:25Z
- **提交信息**: [Bugfix] Avoid FlexAttention recompiles when request counts change (#55888)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [d8d53f1](https://github.com/vllm-project/vllm/commit/d8d53f17c231bf477aa89f25a904f9b7c54fbcb9)

- **作者**: haic0
- **时间**: 2026-09-09T14:50:24Z
- **提交信息**: [Rocm][Kimi-k3] Add pipeline_parallel support for the kimik3 model (#53664)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [4e990df](https://github.com/vllm-project/vllm/commit/4e990dfcec4bd12437961457ec35d8ff862baf22)

- **作者**: Micah Williamson
- **时间**: 2026-09-09T14:49:59Z
- **提交信息**: [ROCm] Bump AITER to v0.1.21.post2 (#55968)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [138d137](https://github.com/vllm-project/vllm/commit/138d137b5b955a5ebee98dfc946ecdd65d7b87ce)

- **作者**: Ronen Schaffer
- **时间**: 2026-09-09T14:45:49Z
- **提交信息**: [Refactor][kv_offload]: rename `block`→`chunk` (#52615)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>

### [9ffb8ce](https://github.com/vllm-project/vllm/commit/9ffb8cea96369e2164af184a10faaa618eaf6b92)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-09T14:38:32Z
- **提交信息**: [CI] Add e2e test for scale-out EC connector flow (#54973)

Signed-off-by: zhouyou9505 <zhouyou9505@gmail.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: zhouyou9505 <zhouyou9505@gmail.com>
Co-authored-by: Cursor Grok 4.6 <noreply@cursor.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [cc4210f](https://github.com/vllm-project/vllm/commit/cc4210f6719e3285fdfe4da862ae04c8dbb77ab1)

- **作者**: Thien Tran
- **时间**: 2026-09-09T14:33:12Z
- **提交信息**: [Perf] Improve BF16x3 router GEMM accuracy and make it default on sm100 (#55899)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [3116c5d](https://github.com/vllm-project/vllm/commit/3116c5d06bfe76501b3dd6b5434bfc7f3274f5e7)

- **作者**: Harry Huang
- **时间**: 2026-09-09T14:32:34Z
- **提交信息**: [Qwen4Exp] Support UVA PLE-offload and Engram tensor parallelism (#54371)

Signed-off-by: huanghaoyan.hhy <huanghaoyan.hhy@alibaba-inc.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [62f3bf5](https://github.com/vllm-project/vllm/commit/62f3bf58a504fa58040d099f6fdd1a6171c90728)

- **作者**: jimmy-adams
- **时间**: 2026-09-09T13:50:41Z
- **提交信息**: [Bugfix][ROCm][DSv4] Skip launch_pdl=True JIT warmup when PDL is unsupported (#56035)

Signed-off-by: jimmy-adams <41593649+jimmy-adams@users.noreply.github.com>

### [e509d32](https://github.com/vllm-project/vllm/commit/e509d32b5a2f3d81dc949ff89f85c4c8f860ae29)

- **作者**: Thomas Ortner
- **时间**: 2026-09-09T13:46:31Z
- **提交信息**: [Transformers backend] Enable QKV-Fuser for Gemma4 (#55690)

Signed-off-by: Thomas Ortner <boh@zurich.ibm.com>
Signed-off-by: Thomas Ortner <bohnstinglthomas@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [08b3e67](https://github.com/vllm-project/vllm/commit/08b3e67b669d18d5bbd14e456b8bb4794916e402)

- **作者**: abrahamzewoudie
- **时间**: 2026-09-09T13:28:24Z
- **提交信息**: [ROCm][Perf] Fix Qwen3-vLLM audio encoder TP when heads are not divisible by TP size (#45900)

Signed-off-by: abrahamzewoudie <azewoudi@amd.com>

### [94848ed](https://github.com/vllm-project/vllm/commit/94848eda600a07c28675f5753a11b2c212c146ed)

- **作者**: Adababy
- **时间**: 2026-09-09T12:37:10Z
- **提交信息**: [Bugfix] Fix unreachable None guard in Molmo2 get_candidate_target_fps (#55893)

Signed-off-by: shaolila <shaolila@buaa.edu.cn>
Co-authored-by: shaolila <shaolila@buaa.edu.cn>

### [c7e9816](https://github.com/vllm-project/vllm/commit/c7e9816c6ab0731165a134fd0a9defed6ab1d748)

- **作者**: Salt Sato
- **时间**: 2026-09-09T09:55:04Z
- **提交信息**: [Bugfix][Rust Frontend] Skip undefined token ids in decode and anchor them zero-width (#55240)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Codex <noreply@openai.com>
Signed-off-by: Feathbow <feathbow@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [474839f](https://github.com/vllm-project/vllm/commit/474839f8469ed4d47bffa18c6a063547a148bf2c)

- **作者**: wliao2
- **时间**: 2026-09-09T09:13:48Z
- **提交信息**: [CI/Build] Upload CPU nightly image to Docker Hub (#55163)

Signed-off-by: Liao, Wei <wei.liao@intel.com>

### [de650b5](https://github.com/vllm-project/vllm/commit/de650b55af53d7fd1677cc0cbaa0fad97b78286e)

- **作者**: Jefrey Cayab
- **时间**: 2026-09-09T09:08:12Z
- **提交信息**: [Docs] Update README.md MkDocs to give option to run dev-server on different port. (#54584)

Signed-off-by: jcayab <42927334+jcayab@users.noreply.github.com>
Signed-off-by: Jefrey Cayab <jcayab@gmail.com>
Signed-off-by: Jefrey Cayab <42927334+jcayab@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [68dcc4f](https://github.com/vllm-project/vllm/commit/68dcc4fd86b11d1cfa228cfc2c9d2b9706ba7af3)

- **作者**: Wen Zhou
- **时间**: 2026-09-09T08:54:54Z
- **提交信息**: [Rust Frontend] Make --max-model-len optional for the render server (#55328)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Wen Zhou <wenzhou@redhat.com>

### [5acd959](https://github.com/vllm-project/vllm/commit/5acd95906b7c7a54dde89396d2bb06fe28ebeed0)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-09T08:47:45Z
- **提交信息**: [Bugfix] Exclude DP token padding from draft attention metadata (#55458)

Signed-off-by: khluu <khluu000@gmail.com>
Signed-off-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [114abd1](https://github.com/vllm-project/vllm/commit/114abd1c1131ceb5e2364b77f114ddca2957c734)

- **作者**: Nikhil Kulkarni
- **时间**: 2026-09-09T07:51:45Z
- **提交信息**: [Bugfix][Frontend] Reject unsupported Responses API input items with 400 instead of 500 (#55974)

Signed-off-by: Nikhil Kulkarni <nikhilkulkarni1755@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-10
**监控日期**: 2026-09-09
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6741
- **最后更新**: 2026-09-10T00:13:51Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 16
- **主要提交者**: Sparks, NumberWan, chi030303

## AI分析总结

# vllm-omni 昨日提交分析报告

## 一、主要更新类型分布

本次提交共17条，涵盖Bug修复（5条）、模型功能优化（4条）、CI/CD与硬件适配（4条）、文档更新（3条）、性能优化（1条）。整体呈现“修复为主、功能为辅、文档跟进”的节奏，符合项目从快速扩张转向稳定打磨的阶段特征。

## 二、关键变更点与项目方向关联

**硬件生态扩展**是本次提交的核心主线。XPU平台W8A16 FP8线性层输出形状修复、Ascend NPU 310/A5系列bug修复、ROCm平台SenseNova与CUDA/NPU标签路由对齐，共同指向项目“多硬件后端统一”的战略目标。这些修复虽属底层细节，却是保证vllm-omni在Intel、华为、AMD等异构芯片上提供一致体验的必要条件。

**多模态模型能力增强**同样突出。MOSS-TTS本地批处理与流式编解码优化、Wan2.2 S2V跳过无用帧打包、LTX-2.5 DiffVAE算子优化、MiniMax-H3时序回调机制，覆盖语音、视频、扩散模型三大模态方向，直接呼应README中“omni-modality”的核心定位。

**API层健壮性提升**体现在音频生成请求的字段校验器新增，以及引擎层将重叠设备阶段分组为顺序初始化组件，后者对多设备流水线并行场景的稳定性意义重大。

## 三、项目影响与潜在意义

这批提交表明vllm-omni正从“能跑”迈向“跑得稳、跑得快、跑得广”。硬件修复降低了特定芯片用户的使用门槛，模型优化提升了推理效率，CI改进则保障了多后端并行开发的可持续性。Qwen3-Omni NVFP4后端修复的保留，暗示项目对低精度推理路线的持续投入。

## 四、值得关注的技术点

- **W8A16 FP8线性层**在XPU上的N-D形状恢复，涉及张量布局与硬件指令集的深层交互
- **MOSS-TTS流式编解码**优化，对低延迟语音交互场景有直接价值
- **LTX-2.5 DiffVAE专用算子**，体现对视频生成管线的端到端性能调优思路
- **设备阶段分组初始化**机制，为大规模多卡部署提供了更稳健的启动流程
- **FA3与torch 2.13的兼容性修复**，反映项目对上游依赖变化的快速响应能力

## 五、对项目发展的综合影响

结合README定位，vllm-omni致力于成为“人人可用的多模态模型服务框架”。昨日提交在三个维度推动这一愿景：**广度**上通过XPU/Ascend/ROCm修复扩大硬件覆盖；**深度**上通过TTS、视频生成等模型优化提升专业场景竞争力；**稳度**上通过API校验、引擎初始化重构和CI规范化夯实企业级应用基础。文档更新（如Qwen3-TTS在A100上的部署数据、FLUX.1-schnell在RTX 5090上的配方）则持续降低新用户的上手成本。整体来看，项目正处于“多硬件适配深化+核心模态能力精进”的良性发展阶段，为后续更广泛的omni-modal模型接入奠定了扎实基础。

## 详细提交记录

### [51cf142](https://github.com/vllm-project/vllm-omni/commit/51cf142bc1dfa372f2c61cfee44535f61afd93de)

- **作者**: Joshna-Medisetty
- **时间**: 2026-09-09T22:11:31Z
- **提交信息**: [Bugfix][XPU] Restore N-D output shape for W8A16 FP8 linear (#7301)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Signed-off-by: Joshna-Medisetty <joshna.medisetty@intel.com>

### [b02862b](https://github.com/vllm-project/vllm-omni/commit/b02862beee2f086e7f46df5aff3ca06026041045)

- **作者**: Sy03
- **时间**: 2026-09-09T20:02:12Z
- **提交信息**: [Model] Optimize MOSS-TTS Local batched execution and streaming codec (#7202)

Signed-off-by: Sy03 <1370724210@qq.com>

### [504e5a6](https://github.com/vllm-project/vllm-omni/commit/504e5a6a6e7d3d00105a1c04ba5bd84fd62d5d15)

- **作者**: bojiang-li
- **时间**: 2026-09-09T18:48:41Z
- **提交信息**: [Doc] Add dual DGX Spark MiniMax-H3 results (#7343)

Signed-off-by: bojiang-li <327132355+bojiang-li@users.noreply.github.com>

### [6fb7b0a](https://github.com/vllm-project/vllm-omni/commit/6fb7b0a05e3758e41e3871804598cea18a0b42fb)

- **作者**: hyw
- **时间**: 2026-09-09T14:34:46Z
- **提交信息**: [Model] Skip unused frame packing in Wan2.2 S2V (#7155)

Signed-off-by: hyw <yuweih205@gmail.com>

### [b9932aa](https://github.com/vllm-project/vllm-omni/commit/b9932aa17b0ea5c5e8ec49681eef656403285344)

- **作者**: andyluo7
- **时间**: 2026-09-09T14:32:38Z
- **提交信息**: [CI/Build][ROCm] Normalize SenseNova paged-decode hardware markers (#6935)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [06f6769](https://github.com/vllm-project/vllm-omni/commit/06f67695f1819f795956b8d51f5c982aa082937d)

- **作者**: shiyichuan
- **时间**: 2026-09-09T14:05:44Z
- **提交信息**: [CI/Build] Avoid duplicate stage CLI deploy config (#7007)

Signed-off-by: mershi <mershi@tencent.com>
Co-authored-by: mershi <mershi@tencent.com>

### [c94cf4d](https://github.com/vllm-project/vllm-omni/commit/c94cf4ddde3cddf28fb02fbe27029824ae5ad6c8)

- **作者**: andyluo7
- **时间**: 2026-09-09T13:47:15Z
- **提交信息**: [CI][ROCm] Match CUDA/NPU L2/L3 label routing (#6966)

Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [0e60250](https://github.com/vllm-project/vllm-omni/commit/0e602509aa9460cedca2de45094e6ea1d2be47ba)

- **作者**: Shaun Walsh
- **时间**: 2026-09-09T13:38:42Z
- **提交信息**: [BugFix] Add field validators for /v1/audio/generate request (#4741)

Signed-off-by: Shaun Walsh <shaunwalsh24@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Nick Cao <ncao@redhat.com>

### [2f1845f](https://github.com/vllm-project/vllm-omni/commit/2f1845fa4e74d78609a2c301d3b843628cbf6fb8)

- **作者**: kunkun
- **时间**: 2026-09-09T12:35:16Z
- **提交信息**: fix: reserve Qwen3-Omni NVFP4 backend fix (#7200)

Signed-off-by: kunkunblueberry <1833921874@qq.com>

### [7c1b1e4](https://github.com/vllm-project/vllm-omni/commit/7c1b1e4189d0dbd26a6ecdb05dc20426a6078a24)

- **作者**: Zheng Wengang
- **时间**: 2026-09-09T12:25:41Z
- **提交信息**: [Bugfix][Engine] Group overlapping device stages into one sequential init component (#7328)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [6e79d58](https://github.com/vllm-project/vllm-omni/commit/6e79d582e3c4a4da4a159904125f3de7a6cbae2b)

- **作者**: zyz111222
- **时间**: 2026-09-09T11:03:09Z
- **提交信息**: [Bugfix][Ascend] fix npu 310/a5 bugs (#6685)

Signed-off-by: zouyizhou <zouyizhou@huawei.com>

### [038c9b9](https://github.com/vllm-project/vllm-omni/commit/038c9b948fbf10e99d3167c18a6a22c20049f7f5)

- **作者**: NumberWan
- **时间**: 2026-09-09T10:20:34Z
- **提交信息**: [Bugfix] Resolve #6931 hub FA3 on torch 2.13 via kernels 0.16.1 (#7185)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [cdd4638](https://github.com/vllm-project/vllm-omni/commit/cdd4638b17f86db33a3f798dba468a7aef7bc76b)

- **作者**: Bo Li
- **时间**: 2026-09-09T09:58:42Z
- **提交信息**: [Feature][Diffusion] Expose detailed pipeline timings (#6822)

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [ecdd762](https://github.com/vllm-project/vllm-omni/commit/ecdd762ff57640b2007ed84e9f681c18a872e28d)

- **作者**: Anjie Hou
- **时间**: 2026-09-09T08:40:32Z
- **提交信息**: [2/N] Add a minimal temporal chunk callback for MiniMax-H3 (#7017)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [ffa991b](https://github.com/vllm-project/vllm-omni/commit/ffa991b24fcf9540126ce574f9c7b8fa174af96d)

- **作者**: Mu GuanLin
- **时间**: 2026-09-09T08:31:16Z
- **提交信息**: [Perf][Model] Add optimized LTX-2.5 DiffVAE operators (#7308)

Signed-off-by: mglyn <1203789601@qq.com>

### [c66df06](https://github.com/vllm-project/vllm-omni/commit/c66df06c0ffd48cf4f7a0b01434673a3cd7467b5)

- **作者**: chi030303
- **时间**: 2026-09-09T07:56:14Z
- **提交信息**: [Doc] Qwen3-TTS: add 0.6B on 1x A100 40GB (#7289)

Signed-off-by: chi030303 <106855944+chi030303@users.noreply.github.com>

### [7712701](https://github.com/vllm-project/vllm-omni/commit/7712701578d8359b5af958bb2df9023c90e21a6d)

- **作者**: Sparks
- **时间**: 2026-09-09T07:54:46Z
- **提交信息**: [Doc] [Recipe] Add FLUX.1-schnell recipe for RTX 5090 32GB (#7299)

Signed-off-by: Sparks-M <41097544+Sparks-M@users.noreply.github.com>

---
