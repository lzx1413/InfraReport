# GitHub Stars 合并报告 - 2026-09-12

**合并日期**: 2026-09-13
**监控日期**: 2026-09-12
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


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2205
- **最后更新**: 2026-09-11T20:28:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2805
- **最后更新**: 2026-09-12T12:06:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2246
- **最后更新**: 2026-09-12T08:34:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6387
- **最后更新**: 2026-09-12T19:16:39Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 8
- **主要提交者**: Alex Yang, Josh Park, Jimmy Zhou

## AI分析总结

## FlashInfer 昨日更新总结

### 一、主要更新类型

昨日共 10 个提交，以 **Bug 修复** 为主，辅以 **功能新增**、**性能优化** 与 **重构**，覆盖 MoE、GEMM、注意力、线性注意力、通信测试与 CI 发布流程。

### 二、关键变更点

- **MoE 量化重构**（#5061）：删除 `QuantVariant`，改为按 MMA `(weight, activation)` 对显式派发 `QuantConfig`，推动量化配置从隐式枚举走向显式、可组合的矩阵对模型。
- **MoE 占用校验修复**（#4847）：`queryOccupancyForConfig` 不再对 TMA warp-specialized 配置无条件返回 1，而是真实探测派发，避免无效 tactic 污染自动调优。
- **cuTile GEMM 稳定性**（#4459、#5155）：前者按固定键排序并列候选以降低选型抖动；后者跳过 SM10x 上会触发粘性 launch failure 的 `num_ctas=2/occupancy=2` 候选。
- **Sage 注意力修复**（#5127）：SM120 特化从 7 扩到 25，tensor map 改为按值传递，消除工作区复用导致的 CUDA 故障。
- **线性注意力新增 cuDNN 后端**（#4968）：为 GDN 提供第二个后端，性能与 FlashInfer 互有胜负。
- **Cake MegaMoE 后端**（#5148、#4819）：前者优化 BF16 激活 + MXFP8 专家权重的 EP16 后端，采用 `[N32, N16, N16]` 行调度与权重瓦片复用，稳态下每次 `run` 仅启动两个内核；后者引入可复用工作区机制与经 SHA-256 源身份校验的 SM100a 原生 reducer。
- **CI 与测试**（#4472、#4205）：rc 标签正确标记为 prerelease；分布式测试失败时报告每个 rank 的退出状态与独立日志。

### 三、对项目的影响

- 量化派发重构是**破坏性 API 变更**，但换来更清晰的语义，利于长期维护与文档一致性。
- 多项修复直指**自动调优噪声与上下文污染**，提升内核选择的可靠性与可复现性。
- cuDNN 后端引入**多后端竞争**，为线性注意力提供性能与鲁棒性备选。
- 工作区 API 使权重预处理不再重复，利于多容量场景与 CUDA Graph 使用，降低端到端延迟。
- CI/测试改进提升**发布正确性**与**故障可诊断性**，降低维护成本。

### 四、值得关注的技术点

- TMA warp-specialized 的 workspace-query 探测复用 `calcMaxWorkspaceSize` 的优雅跳过惯用法。
- cuTile `occupancy=2` 疑似上游 codegen bug（粘性 launch failure 无法捕获重试），值得上报 NVIDIA。
- `const __grid_constant__` 按值传 tensor map，使每次 eager 调用/图捕获自持描述符，免除工作区缓存。
- MXFP8 权重采用交错布局 + 分块 E8M0 scale，配合 TMA 描述符在会话构造时一次性初始化。
- Reducer 契约明确：输入 `[capacity, 6, 4096]` BF16、输出 `[capacity, 4096]`，要求 128 字节对齐、非重叠、零 token 为 host no-op。
- Cake 后端仍为 JIT-only、实验性，不参与 AOT 打包与自动后端选择，且明确不支持 CUDA Graph 捕获。

### 五、结合项目背景的发展影响

FlashInfer 定位为**高性能 GPU 推理内核库**。本批提交延续其核心诉求：在 MoE、GEMM、注意力等关键路径上追求**正确性、稳定性与可复现性能**。量化派发重构与多后端引入扩展了可服务模型范围（如 Qwen3、GDN），Cake MegaMoE 的优化与工作区机制则强化了专家并行这一现代大模型推理核心场景的成熟度。整体推动项目从“能跑”走向“可信赖、可维护”的生产级推理基础设施，并为后续 MoE 后端稳定化与更广泛硬件（SM100a/SM103a）适配奠定基础。

## 详细提交记录

### [7629d21](https://github.com/flashinfer-ai/flashinfer/commit/7629d2181a8858d7acd45820cb05f3098d76a895)

- **作者**: SSH
- **时间**: 2026-09-12T19:16:34Z
- **提交信息**: fix(moe): validate TMA warp-specialized configs in queryOccupancyForConfig (#4847)

## 📌 Description

`MoeGemmRunner::queryOccupancyForConfig` returns 1 unconditionally for
every TMA warp-specialized config. A TMA WS config can still be rejected
at dispatch time — on SM120 NVFP4 grouped GEMM (bf16 activations × nvfp4
weights, the Qwen3.8-Flash-Next serving shape), 12 of the 60 offered
tactics throw `Unsupported tile shape config 128128256 / 256128128 for
MoE gemm` from the tile-shape switch and can never launch. Because
occupancy reported them as runnable, `get_valid_tactics`' occupancy
pre-filter passed them through, and every autotuning pass ran them into
a host-side exception: profiling noise, wasted tuning time, and polluted
failed-tactic statistics (they were part of what made #4841 so hard to
diagnose).

This PR makes the TMA WS branch of `queryOccupancyForConfig` probe the
real dispatch in workspace-query mode — the same graceful-skip idiom
`calcMaxWorkspaceSize` already uses
(`calcMaxWorkspaceSizeTmaWarpSpecialized` walks
`dispatchMoeGemmSelectTileShapeTmaWarpSpecialized`, which throws for
unsupported tiles, without launching anything) — and reports occupancy 0
when the dispatch rejects the config. Supported configs keep reporting
1, so behavior is unchanged wherever every tile shape is implemented.

Notes:
- The probe uses `EpilogueFusion::NONE` for all configs, matching
`calcMaxWorkspaceSize`'s own loop (tile-shape validity is
fusion-independent).
- Two further SM120 tactics fail later, at cutlass `initialize` with
real problem shapes (`Failed to initialize cutlass TMA WS grouped gemm.
Error: Error Internal`); those need problem-shape context and are
intentionally not covered by this query-time probe — they continue to be
skipped gracefully during profiling as before.
- The probe is guarded to the specializations `calcMaxWorkspaceSize`
itself supports (`isValidTmaWarpSpecializedMOESpecialisation`, not
w4afp8 / wfp4a16 / sm90-mixed-input); everything else keeps the previous
conservative `return 1`.

## 🔍 Related Issues

Fixes the tactic-presentation defect in #4841. (The
generation-corruption half of that issue was root-caused to
sgl-project/sglang#36537, fixed by sgl-project/sglang#36806 — full
analysis in the issue thread — and is not a FlashInfer defect.)

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Verified on SM120 hardware (RTX PRO 6000, driver 595.84) via a JIT
rebuild of `fused_moe_120` with this change, against the NVFP4 config
above (512 experts / top-10 / hidden 2560 / inter 640, bf16 activations,
packed int64 weights):

- `get_tactic_occupancy` now returns 0 for exactly the 12
dispatch-rejected tactics — gemm1 {4, 5, 14, 15} and gemm2 {24, 25, 34,
35, 44, 45, 54, 55} — and they no longer appear in profiling. Before the
change all 60 reported occupancy > 0 and the 12 threw `Unsupported tile
shape config` on every tuning pass.
- The two cutlass-init failures (gemm2 {32, 33}) still surface at
profiling time and are skipped there, as documented above.
- A per-tactic numeric sweep (every surviving tactic × M ∈ {1, 4} ×
routing, vs the default tactic) is unchanged: zero numeric findings.

## Reviewer Notes

The edit is hand-formatted to the file's existing style (Google, 100
cols); local clang-format 16 reflows unrelated lines in this file, so I
left formatting to the CI pre-commit for confirmation. Happy to run any
additional SM100/SM90 checks reviewers want — I only have SM120 hardware
to test on, but the probe path is compile-time guarded to the same
specializations `calcMaxWorkspaceSize` handles.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved dispatch validation for TMA warp-specialized configurations.
* Unsupported configurations are now rejected during occupancy checks
instead of being incorrectly reported as available.
* Preserved support for valid configurations while accounting for the
configured expert count and scaling mode.
* Improved configuration selection by preventing unavailable options
from being chosen during execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: SSHdotCodes <skyler.hoberman@icloud.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

### [7cf0c6c](https://github.com/flashinfer-ai/flashinfer/commit/7cf0c6c7f48cfbbcf1dc1e239f7ed5d06a55c380)

- **作者**: Alex Yang
- **时间**: 2026-09-12T18:48:04Z
- **提交信息**: ci: apply --prerelease to rc in release workflow (#4472)

<!-- .github/pull_request_template.md -->

## 📌 Description

`release.yml` creates every release with a bare `gh release create` and
no `--prerelease`:

```bash
gh release create "$TAG" \
  --title "Release v${{ needs.setup.outputs.version }}" \
  --notes "$NOTES"
```

The GitHub REST API defaults `prerelease: false`, and neither the API
nor `gh` infers pre-release status from the tag name — the "this looks
like a pre-release" auto-detection is a **web-UI affordance only**. So
every `vX.Y.ZrcN` tag was published as a full release.

This matters because a non-prerelease release is eligible for the
**Latest** badge (most recent non-draft/non-prerelease). `v0.6.17rc5`
held Latest for ~28 minutes on 2026-08-07 until `v0.6.16.post3` was
published. Anything resolving "latest release" via the API or download
URLs could land on an rc.

PyPI is unaffected — PEP 440 treats `rcN` as a pre-release on its own,
so `pip install flashinfer-python` already skips them without `--pre`.

This PR detects pre-release tags from the tag name and passes
`--prerelease`, matching what `nightly-release.yml:230` already does
(which is why every `nightly-*` tag is correctly flagged today).
`.postN` is a real release and stays unflagged.

### Backfill already applied

The 16 affected releases were corrected out-of-band with `gh release
edit --prerelease`. Recording them here for the audit trail:

| release | was | now |
|---|---|---|
| `v0.6.17rc5` | full release | pre-release |
| `v0.6.17rc1` | full release | pre-release |
| `v0.6.16rc5` | full release | pre-release |
| `v0.6.16rc4` | full release | pre-release |
| `v0.6.16rc3` | pre-release (fixed by hand earlier) | pre-release |
| `v0.6.13rc2` | full release | pre-release |
| `v0.6.13rc1` | full release | pre-release |
| `v0.6.12rc3` | full release | pre-release |
| `v0.6.12rc2` | full release | pre-release |
| `v0.6.12rc1` | full release | pre-release |
| `v0.6.11rc1` | full release | pre-release |
| `v0.6.10rc1` | full release | pre-release |
| `v0.6.9rc1` | full release | pre-release |
| `v0.6.8rc1` | full release | pre-release |
| `v0.6.0rc2` | full release | pre-release |
| `v0.6.0rc1` | full release | pre-release |

15 of 16 were mislabeled; `v0.6.16rc3` had already been corrected
manually, which is consistent with this having been noticed before but
never fixed at the source. No release notes, assets, or tags were
touched — only the `prerelease` flag. **Latest** still resolves to
`v0.6.17`.

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

This is a CI workflow change with no Python surface, so there is nothing
for `unittest` to cover. Verification done instead:

- Workflow YAML parses; all 7 jobs intact.
- Tag detection verified against real and edge-case tags:

  | tag | result |
  |---|---|
  | `v0.6.17rc5`, `v0.6.0rc1`, `v0.6.13rc2` | pre-release |
| `v1.2.3a1`, `v1.2.3b2`, `v1.2.3.dev1`, `v1.2.3dev1`, `v1.2.3.rc1` |
pre-release |
  | `v0.6.17`, `v0.6.16.post4`, `v0.6.16.post1` | full release |

- `pre-commit run --all-files` passes.
- The `on.pull_request` path trigger on `release.yml` means this PR runs
the release workflow in dry-run mode; that is still in flight.

The remaining box is left unchecked because the repo test suite was not
run locally — the change cannot affect it.

## Reviewer Notes

**Why `a|b|rc|dev` and not `alpha|beta`.** These are the canonical PEP
440 pre-release spellings; `alpha`/`beta` are non-canonical aliases that
normalize away:

```
1.2.3alpha1 -> 1.2.3a1     1.2.3a1 -> 1.2.3a1     1.2.3rc1   -> 1.2.3rc1
1.2.3beta1  -> 1.2.3b1     1.2.3b1 -> 1.2.3b1     1.2.3.dev1 -> 1.2.3.dev1
```

So `a`/`b` are the forms that actually reach `version.txt` and wheel
filenames. A hypothetical `v1.2.3alpha1` tag would not be flagged — but
it is already broken independently, since the built wheel would be
`1.2.3a1` and disagree with the tag. Every tag this repo has ever cut is
`rc` (23) or `post` (21), so this is theoretical either way.

A stricter `packaging.version.Version(...).is_prerelease` parse would be
more faithful, but there is no Python available in this step — hence the
bash pattern.

Also note this PR triggers the full `build-flashinfer-jit-cache` matrix
(3 CUDA × 2 arch, self-hosted, 6h timeout) via the existing path filter.
Happy to cancel if that runner time is unwelcome for a workflow-only
change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Release Management**
* Release creation now automatically identifies tags that follow
pre-release versioning conventions.
* Pre-release versions are labeled as pre-releases, while post-release
versions continue to be published as standard releases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7b4545f](https://github.com/flashinfer-ai/flashinfer/commit/7b4545f5474d7ff433963182b56090c53d3ad048)

- **作者**: Jimmy Zhou
- **时间**: 2026-09-12T18:37:25Z
- **提交信息**: fix[GEMM]: WAR for specific cuTile autotune candidate in mm_bf16 (#5155)

<!-- .github/pull_request_template.md -->

## 📌 Description

`_autotune_configs` offers `num_ctas=2` with `occupancy=2` for every
`cc_major >= 10`. On SM10x parts with >=148 SMs that candidate hits a
cuTile miscompile and fails with a **sticky** `unspecified launch
failure` that destroys the CUDA context — so it cannot be caught and
retried after the launch, and later unrelated calls surface it as
`CUBLAS_STATUS_INTERNAL_ERROR when calling cublasSetStream(...)`. This
skips the candidate before `exhaustive_search`.

Reproduced on GB300 (152 SMs) and B300 SXM6 (148 SMs); B300 PCIe (80
SMs) is unaffected. Present with cuda-tile 1.5.0 and 1.6.0 (latest) on
tileiras 13.3.36, so it is not fixed by a version bump.

Validated on GB300 with the exact command from #4465: completes with
`[PERF] cutile :: 0.025 ms`, exit 0, no context poisoning.

**No perf cost.** `occupancy` 1/4/8 all compile to a byte-identical
cubin, and the driver reports 1 block/SM for the `occupancy=2` variant
as well — the squeeze halves registers (255 -> 128) and shared memory
without achieving any extra residency. The tile stays in the search
space at occupancy 1/4/8, which also still sweep the persistent grid
size (56 / 224 / 448).

## 🔍 Related Issues

Fixes #4465.

The mechanism is unresolved and looks like a cuTile codegen bug rather
than a FlashInfer one; worth filing upstream against
NVIDIA/cutile-python (cf. its #96, a tileiras SIGSEGV also specific to
`occupancy=2`).

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

- The predicate also removes `(256,128, num_ctas=2)` at occupancy=2,
which I measured as *not* faulting. Kept it in because kernels are
compiled per `(M,N,K)` so that result does not generalise, and because
occupancy=2 is strictly worse codegen regardless.
- Not addressed here: the post-search probe loop catches the sticky
error with `except Exception: continue`. That is what turns one bad
candidate into a dead process and the misleading downstream cuBLAS error
— worth a follow-up.
- A config-space regression test (asserts the candidate is gone and the
occupancy 1/4/8 neighbours survive; needs no GPU) is ready if you want
it folded in.

Co-authored-by: Alex Yang <aleyang@nvidia.com>

### [6f4e9e4](https://github.com/flashinfer-ai/flashinfer/commit/6f4e9e4ad319d4b97e1741e489e5737b3b7ea264)

- **作者**: Alex Yang
- **时间**: 2026-09-12T18:04:03Z
- **提交信息**: test(comm): report every rank's fate when a dist worker dies (#4205)

<!-- .github/pull_request_template.md -->

## 📌 Description

When
`tests/comm/test_comm_backend.py::test_torch_dist_backend_collectives`
fails, the evidence we most need is the **first** death — and the
harness was throwing it away. As Julien put it on the #4193 thread: *"we
see one of the processes dying because it can't reach another one,
presumably because it itself died prematurely. The problem is we don't
see why this first failure happened."*

Three concrete losses:

- `for p in procs: assert p.exitcode == 0` stopped at the **first** bad
rank, so later ranks were never inspected. In the #4193 log we learned
rank 2 raised and never found out what rank 3 did — and rank 2 may well
have been a victim rather than the culprit.
- A worker killed by a signal prints **no traceback at all**, so an
OOM-kill or a runner shutdown was indistinguishable from a clean
failure. It surfaced only as "a peer I could not reach".
- All workers shared the parent's stderr, so gloo/c10d output from N
ranks interleaved into something unattributable.

**This PR makes the next occurrence self-explaining.** Each worker gets
its own stdout/stderr file, redirected at the **fd** level — a
Python-level redirect would miss exactly the messages worth having,
since gloo and c10d log from C++ straight to fd 2. On failure every rank
is reported: status, whether it produced a result, and its captured
output. Signal deaths are named, which separates an infrastructure kill
from a test failure at a glance:

```
AssertionError: workers [0, 1, 2, 3] did not exit cleanly:
  rank 0 (pid 68390): STILL RUNNING (timed out), NO RESULT
  rank 1 (pid 68391): KILLED by SIGKILL, NO RESULT
  rank 2 (pid 68392): STILL RUNNING (timed out), NO RESULT
  rank 3 (pid 68393): STILL RUNNING (timed out), NO RESULT
```

The failure is now **bounded**, too. A worker that loses a peer blocks
in its collective until gloo's own 30-minute timeout, which turns a
failure into a CI hang. Past the deadline the survivors are killed and
reported as timed out, with exit codes snapshotted first so the report
says how each worker actually ended rather than how we ended it.

Two smaller robustness fixes in the same harness:

- Drain the result queue **before** `join()`. A worker blocks on exit
until its queue feeder thread has flushed, so join-then-read can
deadlock, and `q.empty()` is unreliable.
- Exercise `barrier()`/`allgather()` on the split sub-group rather than
only checking its rank and size, so a broken sub-group is caught
directly instead of as a downstream crash.

## 🔍 Related Issues

Related to #4193. This does **not** fix that issue and deliberately uses
no closing keyword — it is the instrumentation that should make the next
occurrence diagnosable rather than another round of inference. #4193
should stay open, with its `infra` label intact.

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

`tests/comm/test_comm_backend.py`: 9 passed, 1 skipped (mpi4py not
installed), on both macOS and Linux/x86_64 with CPU-only gloo.

The diagnostics themselves were verified by **fault injection** rather
than by inspection — it would be embarrassing for the instrumentation to
be the thing that is broken next time:

| injected fault | reported |
|---|---|
| rank 1 raises | `rank 1: exited 1` with its full traceback; ranks
0/2/3 as `STILL RUNNING (timed out)` |
| rank 1 `SIGKILL`s itself | `rank 1: KILLED by SIGKILL`; ranks 0/2/3 as
timed-out victims |

Both injected runs failed in ~16 s instead of hanging, confirming the
bound.

## Reviewer Notes

This is deliberately **test-only** — no change under `flashinfer/`. It
was split out of #4195 so it can land on its own merits; the
process-group change that #4195 proposes is unproven and shouldn't hold
this up.

One interaction worth knowing: this PR adds a `barrier()` on the split
sub-group inside the test. That is legitimate coverage, but it also
happens to synchronize the ranks after `Split()`, so it may incidentally
mask the very race #4195 hypothesises. If you want #4193's signature
preserved for observation, that is the line to look at.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Improved distributed test diagnostics with per-process log capture and
clearer failure messages.
* Added timeout handling that terminates stalled processes and reports
relevant log output.
* Expanded collective-operation coverage to validate results within
subgroups.


<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d70a043](https://github.com/flashinfer-ai/flashinfer/commit/d70a043f5edbd0ccb363784ffe7fe97608b2d9a3)

- **作者**: Lee Yong Jun
- **时间**: 2026-09-12T14:21:35Z
- **提交信息**: fix(cutile): stabilize autotune config selection in select GEMMs (#4459)

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Adds a small shared helper and applies it to the `mm_bf16`, `bmm_bf16`,
and `gemm_fp8_nt_groupwise` cuTile paths, with unit tests. Other cuTile
GEMMs (alpha-beta, masked/ragged bmm, block-scaled, grouped FP8) and
FMHA are not touched.

`exhaustive_search` stops sampling a candidate once its error margin
drops below max(1% of mean, 0.5 us). For fast kernels this margin is of
the same order as the gap between the top candidates, so the argmin
decision is made inside the measurement noise. In my testing on an RTX
PRO 6000 Blackwell (SM120) with `mm_bf16` m=1, n=4096, k=4096, the top-2
gap was 0.1 to 0.3 us while the reported margins were 0.4 to 0.5 us, and
11 fresh processes split 6 to 5 between `occupancy=8` and `occupancy=1`.

A candidate is treated as tied with the fastest one when the gap between
their means is within the combined 95% error margins, or within 2% of
the best mean (run-to-run drift of the mean itself is of this order, so
ranking inside that band is noise). Tied candidates are ordered by a
fixed config key, lowest occupancy first, then fewest CTAs, then
smallest tile; the rest keep the latency order. The NaN/Inf probe in the
mm and bmm paths walks the same reordered list, so its fallback follows
the same order.

This reduces run-to-run variance in the selected config; it does not
make the selection fully deterministic, since the tie band still depends
on the measured means and margins.

Preferring the lowest occupancy within a tie seems safe here: when
total_tiles already covers the grid, higher occupancy only adds CTAs
that exit the persistent loop immediately.
## 🔍 Related Issues

<!-- Link any related issues here -->
#4433
## 🚀 Pull Request Checklist

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

12 fresh-process autotune runs of the m=1, n=4096, k=4096 case on SM120
after the change: the winner is `occupancy=1` in 12 of 12 runs. Before
the change, 11 runs split 6 to 5 between two configs.

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Improvements**
* Improved cuTile autotuning to select configurations more consistently
when measured performance is nearly identical.
* Added deterministic tie-breaking for equivalent configurations,
improving reproducibility across runs.
* Improved fallback behavior when candidate validation fails by
selecting the highest-ranked available configuration.

* **Tests**
* Added coverage for latency ties, tolerance handling, clear winners,
ordering independence, preservation of results, and single-result
scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [aeab8e9](https://github.com/flashinfer-ai/flashinfer/commit/aeab8e964bb76675012a2bd2b72bec06502af48a)

- **作者**: eigen
- **时间**: 2026-09-12T11:43:40Z
- **提交信息**: fix(cake_sage_attn): cover Sage combinations and pass tensor maps by value (#5127)

Sage attention could fail to find an exported module for legal parameter
combinations. The binding also assumed caller-owned TMA workspace
contents remained valid: overwriting or recycling that storage could
cause a CUDA fault or silently access the wrong tensors.

Expand the SM120 export from 7 to 25 specializations, covering omitted
and uniform counts, every block-size layout, partial KV tiles, and empty
selections. Pass all four tensor maps by value through `const
__grid_constant__` kernel parameters. Each eager call and captured graph
owns its descriptor values, so attention needs no descriptor workspace
cache or upload kernel. Keep the existing Python
`tma_descriptor_workspace` keyword accepted but unused; an empty tensor
is sufficient.

Add 73 attention cases and six isolated descriptor regressions:
overwritten workspace, stale valid descriptors, recycled views,
interleaved graph replay and eager bindings, ordered streams, and empty
workspace. Tests also verify that workspace contents remain unchanged.
Document count semantics and captured tensor lifetimes.

Validation on RTX PRO 6000 Blackwell Server Edition (SM120):
- All 79 public GPU tests pass in 158.97s, covering all 25
specializations.
- The affected source GPU regression and fresh-binding graph capture
test pass; all 40 contract correctness rows and eight unchanged
performance rows pass.
- Separate Compute Sanitizer runs pass: synccheck 0 errors in 6.127s;
racecheck 0 hazards in 6.575s. Each process has a 20s hard limit.

Three-arm, interleaved cold-L2 CUPTI measurements include the complete
exported FFI GPU execution span. All three versions were measured on the
same GPU in the same run; JIT, allocation, and reference computation are
excluded.

| Case | Cached workspace baseline (µs) | Previous upload fix (µs) |
Current grid-constant ABI (µs) |
| --- | ---: | ---: | ---: |
| B1 H2 S128 | 5.087 | 7.457 | 4.800 |
| Non-contiguous KV4000 | 25.984 | 28.001 | 25.312 |
| Non-contiguous KV4033 | 19.328 | 21.649 | 19.008 |
| B8 H32 S1024, density90 | 221.137 | 223.905 | 218.114 |

CUPTI records one, two, and one kernel activities per call respectively.
The current ABI removes the extra upload launch and has lower median
latency than both prior versions in these four measured cases. These
results replace the earlier table for the upload-based implementation.

Follow-up to #5083.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Improved SM120 Sage block-sparse attention execution with more
reliable tensor-map handling and CUDA device management.
* Added support for per-row, uniform, omitted, empty, and contiguous
block-count modes, including ragged sequence lengths.
* CUDA Graph capture and replay now work more reliably; each captured
launch preserves its own tensor descriptors.
* The compatibility workspace is accepted but no longer required for
descriptor storage.

* **Bug Fixes**
* Strengthened validation for tensor layouts, strides, alignment, scalar
ranges, and empty selections.

* **Tests**
* Added coverage for workspace reuse, stale or empty workspace contents,
stream ordering, and CUDA Graph replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [3a5f57d](https://github.com/flashinfer-ai/flashinfer/commit/3a5f57d749737cc1b7c2f024ff037b8c78bb24fd)

- **作者**: feih-nv
- **时间**: 2026-09-12T09:54:22Z
- **提交信息**: feat(moe): remove QuantVariant and dispatch QuantConfig by MMA pair (#5061)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #4952. Remove `QuantVariant`. Every scheme is an explicit
MMA `(weight, activation)` pair; runners match on `quant.pair`.
`QuantConfig` is a plain `@dataclass(frozen=True)`: omitted axes default
to BF16, knobs stay keyword-only, `init=False` is gone.

**Breaking:** `QuantVariant`, `QuantConfig.from_variant`, and
`QuantConfig(variant=...)` are deleted. Spell the pair
(`QuantConfig(weight=QuantFormat.MXFP4)` is MXFP4×BF16; MXFP4×MXFP8
needs both axes).

| Former `QuantVariant` | `(weight, activation)` |
|---|---|
| BF16 | `(BF16, BF16)` |
| FP8PerTensor | `(FP8PerTensor, FP8PerTensor)` |
| DeepSeekFp8 | `(DeepSeekFp8, DeepSeekFp8)` |
| MxFp8 | `(MXFP8, MXFP8)` |
| NVFP4 | `(NVFP4, NVFP4)` |
| MXFP4 | `(MXFP4, MXFP8)` — TRTLLM W4A8; not MXFP4×MXFP4 |
| MxInt4 | `(MXINT4, BF16)` |
| W4A8 | `(INT4, FP8PerTensor)` — CUTLASS SM90 packed mixed-input,
distinct from MXFP4×MXFP8 |
| Humming | `(MXFP4, FP8PerTensor)` |
| W4A16 | `(MXFP4, BF16)` on TRTLLM / CUTLASS SM90; `(NVFP4, BF16)` on
CuTe-DSL / b12x. There was no `variant=` expansion for this member. |

Activation-matrix labels are always the MMA pair `W×A` (`NVFP4×NVFP4`,
`MXFP4×BF16`, `NVFP4×BF16`). The design-doc table was regenerated. FP4
`prepare_*` helpers default `quant` to NVFP4×NVFP4 in the signature
instead of resolving `None` internally.

## 🔍 Related Issues

#4952

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

CPU tests cover construction, omitted-axis defaults, keyword-only knobs,
`replace`, and repr round-trip. Existing unified-MoE / CUTLASS / FP8 /
b12x / mxfp4 / moe_ep tests now build configs from pairs and select
branches on `quant.pair`. A `pytest_make_parametrize_id` hook in
`tests/moe/conftest.py` (and `tests/moe_ep/`) names `QuantConfig` /
activation parameters (`NVFP4`, `MXFP4xBF16`, `SwiGLU`) instead of
pytest's `variant0`, so test ids stay matchable against nightly. Fuzz
`_DTYPE` key order and seed lock are unchanged. CUDA kernels are
unchanged.

## Reviewer Notes

- Select on `.pair == (W, A)`; a whole-object `==` also compares the
scale-factor knobs.
- `pytest.raises(..., match=)` should match `weight=X, activation=Y`,
not a `QuantConfig(...)` repr.
- `"w4a16"` in the fuzzer is MXFP4×BF16; `"b12x_w4a16"` is NVFP4×BF16.

### [a69ad80](https://github.com/flashinfer-ai/flashinfer/commit/a69ad808f8ff4095df4460cbda86ebcf815aa31d)

- **作者**: Josh Park
- **时间**: 2026-09-12T09:37:08Z
- **提交信息**: Add cuDNN backend for linear attention (#4968)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds cuDNN as a backend for linear attention.

GDN GB200
| heads   | seqs               |  cudnn | fi flashinfer | fi/cudnn |
|---------|--------------------|-------:|--------------:|---------:|
| h16     | 1x2048             |   76.4 |          79.1 |    1.04x |
| h16     | 1x8192             |  138.4 |         130.1 |    0.94x |
| h16     | 1x32768            |  301.4 |         327.1 |    1.09x |
| h16     | 1x131072           |  907.5 |        1050.0 |    1.16x |
| h16     | 2x16384            |  296.4 |         333.0 |    1.12x |
| h16     | 6144+2048          |  130.8 |         136.6 |    1.04x |
| h16     | 4x8192             |  242.9 |         230.7 |    0.95x |
| h16     | 8x1024             |   51.3 |          44.9 |    0.88x |
| h16     | 16x2048            |  145.4 |         147.4 |    1.01x |
| h16     | 1024+7168          |  122.6 |         137.4 |    1.12x |
| h16     | 2048+6144          |  130.9 |         135.3 |    1.03x |
| h16     | 2x4096             |  118.7 |         133.1 |    1.12x |
| h16     | 4096+2048+2048     |  130.4 |         121.6 |    0.93x |
| h16     | 512+1536+2048+4096 |  150.5 |         122.5 |    0.81x |
| h16     | 7168+512+512       |  142.4 |         202.4 |    1.42x |
| h64     | 1x2048             |   84.6 |          68.8 |    0.81x |
| h64     | 1x8192             |  243.6 |         232.5 |    0.95x |
| h64     | 1x32768            |  869.9 |         883.4 |    1.02x |
| h64     | 1x131072           | 3431.4 |        3476.4 |    1.01x |
| h64     | 2x16384            |  449.8 |         478.7 |    1.06x |
| h64     | 6144+2048          |  212.0 |         185.1 |    0.87x |
| h64     | 4x8192             |  467.4 |         492.2 |    1.05x |
| h64     | 8x1024             |  154.8 |         169.0 |    1.09x |
| h64     | 16x2048            |  450.9 |         521.1 |    1.16x |
| h64     | 1024+7168          |  236.7 |         211.2 |    0.89x |
| h64     | 2048+6144          |  213.2 |         185.3 |    0.87x |
| h64     | 2x4096             |  134.6 |         137.8 |    1.02x |
| h64     | 4096+2048+2048     |  152.6 |         198.9 |    1.30x |
| h64     | 512+1536+2048+4096 |  151.0 |         185.1 |    1.23x |
| h64     | 7168+512+512       |  234.8 |         231.9 |    0.99x |
| gva2_8  | 1x2048             |   62.4 |          72.3 |    1.16x |
| gva2_8  | 1x8192             |   92.0 |         110.9 |    1.21x |
| gva2_8  | 1x32768            |  177.3 |         210.0 |    1.18x |
| gva2_8  | 1x131072           |  499.7 |         565.3 |    1.13x |
| gva2_8  | 2x16384            |  187.6 |         199.6 |    1.06x |
| gva2_8  | 6144+2048          |  101.6 |         105.7 |    1.04x |
| gva2_8  | 4x8192             |  176.0 |         215.4 |    1.22x |
| gva2_8  | 8x1024             |   57.2 |          39.8 |    0.70x |
| gva2_8  | 16x2048            |   76.3 |          70.8 |    0.93x |
| gva2_8  | 1024+7168          |  107.1 |         110.7 |    1.03x |
| gva2_8  | 2048+6144          |  101.7 |         107.9 |    1.06x |
| gva2_8  | 2x4096             |   89.4 |          98.4 |    1.10x |
| gva2_8  | 4096+2048+2048     |  102.4 |         109.4 |    1.07x |
| gva2_8  | 512+1536+2048+4096 |  100.9 |         110.9 |    1.10x |
| gva2_8  | 7168+512+512       |  107.9 |         116.4 |    1.08x |
| gva4_8  | 1x2048             |   62.6 |          73.7 |    1.18x |
| gva4_8  | 1x8192             |   92.7 |         113.0 |    1.22x |
| gva4_8  | 1x32768            |  178.9 |         211.8 |    1.18x |
| gva4_8  | 1x131072           |  503.4 |         567.7 |    1.13x |
| gva4_8  | 2x16384            |  188.9 |         202.6 |    1.07x |
| gva4_8  | 6144+2048          |  102.5 |         106.6 |    1.04x |
| gva4_8  | 4x8192             |  176.9 |         223.1 |    1.26x |
| gva4_8  | 8x1024             |   57.7 |          40.1 |    0.69x |
| gva4_8  | 16x2048            |   77.0 |          71.6 |    0.93x |
| gva4_8  | 1024+7168          |  107.8 |         112.3 |    1.04x |
| gva4_8  | 2048+6144          |  102.7 |         109.2 |    1.06x |
| gva4_8  | 2x4096             |   90.0 |         100.3 |    1.11x |
| gva4_8  | 4096+2048+2048     |  103.2 |         111.5 |    1.08x |
| gva4_8  | 512+1536+2048+4096 |  101.8 |         112.2 |    1.10x |
| gva4_8  | 7168+512+512       |  108.8 |         117.2 |    1.08x |
| gva4_16 | 1x2048             |   75.6 |          77.1 |    1.02x |
| gva4_16 | 1x8192             |  132.9 |         127.4 |    0.96x |
| gva4_16 | 1x32768            |  289.9 |         321.9 |    1.11x |
| gva4_16 | 1x131072           |  876.8 |        1036.9 |    1.18x |
| gva4_16 | 2x16384            |  286.3 |         327.7 |    1.14x |
| gva4_16 | 6144+2048          |  126.0 |         130.0 |    1.03x |
| gva4_16 | 4x8192             |  243.2 |         232.5 |    0.96x |
| gva4_16 | 8x1024             |   48.0 |          43.2 |    0.90x |
| gva4_16 | 16x2048            |  140.1 |         141.4 |    1.01x |
| gva4_16 | 1024+7168          |  118.1 |         133.2 |    1.13x |
| gva4_16 | 2048+6144          |  126.0 |         131.6 |    1.04x |
| gva4_16 | 2x4096             |  117.9 |         128.2 |    1.09x |
| gva4_16 | 4096+2048+2048     |  125.5 |         122.8 |    0.98x |
| gva4_16 | 512+1536+2048+4096 |  150.6 |         123.2 |    0.82x |
| gva4_16 | 7168+512+512       |  137.8 |         205.6 |    1.49x |

KDA GB200
| heads | seqs            |  cudnn | fi cute-dsl | fi/cudnn |
|-------|-----------------|-------:|------------:|---------:|
| h1    | 1x131072        | 1087.2 |      3615.1 |    3.33x |
| h4    | 1x32768         |  323.3 |       946.2 |    2.93x |
| h4    | 1x131072        | 1095.1 |      3732.3 |    3.41x |
| h4    | 4x32768         |  540.2 |      1071.5 |    1.98x |
| h4    | 24576+8192      |  209.4 |       725.4 |    3.46x |
| h8    | 1x32768         |  324.8 |       984.9 |    3.03x |
| h8    | 1x65536         |  582.0 |      1951.1 |    3.35x |
| h8    | 1x131072        | 1096.0 |      3886.2 |    3.55x |
| h8    | 16384+4096+4096 |  269.2 |       524.5 |    1.95x |
| h16   | 1x2048          |  102.4 |        81.3 |    0.79x |
| h16   | 1x8192          |  189.9 |       279.3 |    1.47x |
| h16   | 1x32768         |  534.5 |      1063.9 |    1.99x |
| h16   | 1x65536         |  993.0 |      2116.0 |    2.13x |
| h16   | 1x131072        | 1911.0 |      4216.3 |    2.21x |
| h16   | 2x16384         |  581.4 |       619.8 |    1.07x |
| h16   | 6144+2048       |  201.8 |       224.6 |    1.11x |
| h16   | 4x8192          |  571.0 |       400.1 |    0.70x |
| h16   | 8x1024          |  111.2 |        75.7 |    0.68x |
| h16   | 16x2048         |  293.3 |       247.8 |    0.84x |
| h16   | 1024+7168       |  194.0 |       252.4 |    1.30x |
| h16   | 4096+2048+2048  |  202.0 |       169.4 |    0.84x |
| h32   | 1x8192          |  323.7 |       318.2 |    0.98x |
| h32   | 1x32768         | 1097.8 |      1218.0 |    1.11x |
| h32   | 4x8192          |  520.4 |       463.9 |    0.89x |
| h64   | 1x2048          |  178.7 |       113.3 |    0.63x |
| h64   | 1x8192          |  571.5 |       393.7 |    0.69x |
| h64   | 1x32768         | 2065.8 |      1533.4 |    0.74x |
| h64   | 1x131072        | 7794.5 |      6158.8 |    0.79x |
| h64   | 4x8192          |  994.9 |       907.4 |    0.91x |
| h64   | 8x1024          |  304.0 |       260.2 |    0.86x |
| h64   | 16x2048         |  908.9 |       832.4 |    0.92x |
| h96   | 1x8192          |  573.8 |       461.5 |    0.80x |
| h96   | 1x32768         | 2028.1 |      1781.4 |    0.88x |
| h96   | 4x8192          | 1467.9 |      1353.6 |    0.92x |

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

* **New Features**
* Added cuDNN-backed linear-attention APIs for GDN, GDN-2, GDP, and
recurrent KDA operations.
* Added public GDN-2 and GDP prefill APIs, with backend selection and
state handling.
* Added cuDNN backend support for existing GDN and recurrent KDA
operations.
  * Added trace support and fixtures for GDN-2 and GDP operations.

* **Documentation**
* Added API documentation covering supported operations, hardware,
requirements, and constraints.

* **Tests**
* Added extensive correctness, validation, layout, determinism, and CUDA
graph coverage for cuDNN backends.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7169776](https://github.com/flashinfer-ai/flashinfer/commit/7169776e1cb9f0d56d13e29e50c0e4e502f1108b)

- **作者**: Haozheng Fan
- **时间**: 2026-09-12T08:31:47Z
- **提交信息**: perf(cake_mega_moe): optimize BF16 x MXFP8 MegaMoE EP16 backend (#5148)

## 📌 Description

Optimizes the existing experimental exact-SM103a `CakeMxfp8MegaMoeEp16`
backend for BF16 activations and outputs with MXFP8 expert weights. The
checked-in CUDA device sources and binding are generated from the final
Cake
program. The public API and explicit opt-in behavior remain unchanged.

### API behavior

- Supports 16 expert-parallel ranks, 512 global experts, top-k 8, hidden
size
  3072, intermediate size 5120, and 16/32/64 tokens per rank.
- `preprocess_cake_mxfp8_megamoe_ep16_weights` converts rank-local BF16
expert
weights to the interleaved MXFP8 weight and blocked E8M0 scale layouts
used
  by the generated kernels.
- `CakeMxfp8MegaMoeEp16` validates immutable routing at construction.
General
expert assignments are accepted when every expert has at most 64 routes
  across all ranks.
- Each `run` submits on the current PyTorch CUDA stream without
allocating and
writes to `session.workspace_output`. Calls on a session must be
serialized
  on one stream.
- CUDA Graph capture is intentionally unsupported.
- The backend remains JIT-only, explicitly experimental, absent from AOT
  packaging, and unavailable through automatic backend selection.

### Export and kernel design

This PR is the complete FlashInfer export of the final Cake-generated
program.
The generated source closure contains the fused model kernel and ordered
reduction kernel used by the backend.

TMA descriptors are initialized once when the session is constructed.
Each
steady-state `run` then launches exactly two model kernels: one fused
publication, dispatch, FC1, SwiGLU, FC2, and direct route-return kernel,
followed by the ordered top-k reducer.

The retained optimizations are:

- A physical `[N32, N16, N16]` row schedule provides capacity 64 while
executing overflow segments only when expert load exceeds 32 or 48
routes.
- Transformed MXFP8 weight tiles are reused across active row segments
instead
  of being reloaded and transformed for each segment.
- FC1 and FC2 work are flattened and balanced over 72 two-CTA clusters
(144 CTAs), with 384 threads per CTA and 75 KiB of dynamic shared
memory.
- Dispatch groups routes by source token so a remote BF16 hidden row is
fetched
once per destination owner and fanned out to its locally owned route
slots.
- FC2 contributions are returned directly to their source `(token, top-k
slot)`
  buffers, removing an owner-local materialization and copy traversal.
- CTA-leader synchronization, streamlined return coordination, and
right-sized
warp-role register budgets reduce synchronization and resource overhead.
- Stable positional bindings, explicit PyTorch/TVM-FFI stream bridging,
and
one-time descriptor setup remove repeated steady-state host preparation.

The manifest records the generated device translation units and binding
as one
content-addressed closure. The JIT loader verifies every file and the
aggregate
closure identity before building them.

### Validation

The generated device-source candidate was validated on 16 NVIDIA GB300
GPUs
using the complete EP16 configuration.

- All six balanced and hot-expert configurations passed BF16 numerical
  correctness, comparison-state equality, and input-immutability checks.
- Three fresh distributed processes passed all six configurations, with
32
consecutive bitwise-stable launches per process and matching per-rank
output
  and launch fingerprints.
- End-to-end validation completed on 16/16 ranks.
- Compute Sanitizer `synccheck` and `memcheck` completed on 16/16 ranks
with
  zero reported errors.
- The public CUDA 13.3 JIT build compiled all three device translation
units
  and the binding into the exact-SM103a module.
- Focused tests pass 15/15 without hardware; the SM103 EP16 test
additionally
covers the 64-route hot-expert tail, all eight route slots,
preprocessing and
scale layouts, routing validation, the binding ABI, and repeated
results.

### Performance

Measurements are paired, same-session CUPTI A/B runs on 16 NVIDIA GB300
GPUs
with EP16. Values are maximum-rank GPU-span medians across three groups,
with
100 ms warmup and a 1,000 ms measurement budget per arm per group. The
baseline
is the BF16 x MXFP8 reference implementation. CUDA Graphs were not used.

| Routing | Global tokens | Tokens/rank | Reference (ms) | This PR (ms)
| Speedup |
| --- | ---: | ---: | ---: | ---: | ---: |
| balanced | 256 | 16 | 1.326420 | 1.162211 | 1.141290x |
| balanced | 512 | 32 | 1.3156025 | 1.176719 | 1.118026x |
| balanced | 1024 | 64 | 1.322886 | 1.1649745 | 1.135549x |
| hot-expert | 256 | 16 | 1.321246 | 1.136386 | 1.162674x |
| hot-expert | 512 | 32 | 1.310207 | 1.157282 | 1.132142x |
| hot-expert | 1024 | 64 | 1.283619 | 1.217985 | 1.053887x |
| **Geometric mean** | | | | | **1.123400x** |

Every measured row improves over the reference. An independent
qualification
run reproduced a 1.130282x geometric-mean speedup, including 1.137746x
for the
hot-expert T=1024 case.

## 🔍 Related Issues

Related to #4969.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request,
please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see
> [the pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #4969
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
tests/experimental/test_cake_mxfp8_megamoe_ep16.py
```

## Reviewer Notes

Please focus on the generated-source closure, the capacity-64
mixed-width route
layout, and the one-time setup/two-kernel steady-state boundary. CUDA
Graph
capture is intentionally rejected.

Signed-off-by: Haozheng Fan <hzfan@apache.org>

### [cbb7912](https://github.com/flashinfer-ai/flashinfer/commit/cbb79124f304d0fa82c8ad47e33c215f229e0f62)

- **作者**: eigen
- **时间**: 2026-09-12T07:27:55Z
- **提交信息**: feat(cake_mega_moe): add reusable MegaMoE workspaces and an SM100a reducer (#4819)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR lets one MegaMoE layer reuse transformed weights with multiple
explicit,
reusable workspace capacities.

It also adds a source-identity-validated SM100a native reducer for the
validated
BF16 TopK-6, hidden-size-4096 configurations with workspace capacities
256 and
4096. Unsupported configurations retain the existing reduction path.

### Runtime contract

- input partials: contiguous BF16 `[capacity, 6, 4096]`
- output: contiguous BF16 `[capacity, 4096]`
- supported native-reducer capacities: 256 and 4096
- live rows: `0 <= num_tokens <= capacity`
- exact target: SM100a with CUDA 12.8 or newer
- launches on the caller's current CUDA stream; zero tokens is a host
no-op
- input and output must be 128-byte aligned and non-overlapping

The bundled source and manifest are checked against fixed SHA-256
identities
before compilation. Runtime validation fails closed on architecture,
dtype,
shape, device, alignment, overlap, or token-count mismatch.

### Workspace API

- `MoEEpMegaLayer.create_workspace(max_tokens_per_rank=...)` creates a
  layer-bound capacity profile; callers do not construct
  `MoEEpMegaWorkspace` directly
- `forward(..., workspace=handle)` selects the capacity profile without
repeating weight preprocessing; omitting it preserves the lazy default
path
- supplying a workspace does not change output ownership: `forward()`
returns
  an owned tensor by default
- `return_workspace_view=True` explicitly opts into a borrowed,
stable-address
  workspace view on supporting backends for CUDA Graph use
- each layer permits one live handle per capacity; an explicit
default-capacity
  handle adopts the same logical default profile instead of acquiring an
  aliasing pool reference
- creation and destruction are EP collectives and must happen in the
same order
  on every rank; cleanup is explicit through `handle.destroy()` or
  `layer.destroy()`, not a context manager or Python garbage collection
- compatible layers may share process-pooled physical storage, so
profiles are
  capacity choices rather than independent concurrency lanes

The reducer generator, loader, readiness check, and launcher are
exported from
the low-level `flashinfer.jit` integration surface and are included in
the AOT
source inventory. Normal callers use the reducer through
`MoEEpMegaLayer.forward()` rather than a new top-level operator.

### Performance: identical reduction work

B200, BF16, CUPTI activity timing with cold L2, 20 dry runs and 100
measured
runs per arm and shape. The frozen prior native, actual delivered native
binary, and source-hash-locked vendored CuTeDSL reducer are interleaved
in
four rotating blocks of 5 dry and 25 measured runs in one process.
Allocation, input preparation, zero-fill, and compilation are outside
timing.

All three process the same live `T × 6 × 4096` values, launch `4 × T`
CTAs,
and perform the same 56 KiB of logical input/output traffic per token.
The launch grid is verified from each implementation's source and
binding.

| live tokens | workspace capacity | prior native (ms) | new native (ms)
| matched CuTeDSL (ms) | prior/new | CuTeDSL/new |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | 256 | 0.0024000 | 0.0018240 | 0.0022720 | 1.315789x | 1.245614x |
| 8 | 256 | 0.0025600 | 0.0019845 | 0.0024960 | 1.289997x | 1.257748x |
| 64 | 256 | 0.0032000 | 0.0027520 | 0.0032000 | 1.162791x | 1.162791x |
| 128 | 256 | 0.0038090 | 0.0035200 | 0.0039680 | 1.082102x | 1.127273x
|
| 256 | 256 | 0.0052160 | 0.0048000 | 0.0051840 | 1.086667x | 1.080000x
|
| 4096 | 4096 | 0.0376155 | 0.0373115 | 0.0402230 | 1.008148x |
1.078032x |
| Geometric mean | — | 0.004949022519 | 0.004295283458 | 0.004966902866
| 1.152199x | 1.156362x |

The new schedule uses 256 threads with four BF16 values per thread
instead
of 128 threads with eight. It retains ordered round-to-nearest FP32
accumulation without FTZ, while reducing registers from 36 to 24. The
delivered binary has six 64-bit no-allocate loads, ten packed FP32 adds,
one 64-bit store, and no stack/shared/local memory or spills.

The geometric-mean latency reduction is 13.2% versus the prior native
and
13.5% versus matched CuTeDSL. Gains are concentrated in decode; T4096 is
already memory-bound and improves only 0.8% over the prior native.
These are reducer-kernel results, not end-to-end MoE speedups.

The prior native is frozen from public revision
`1624aaf9cd6c32b246be1028b51ae4e1afe5c8eb` (CUDA SHA-256
`a0d7bab5d380023d9cc8983fb812ba551157d941e452c5f42da5ffca01e087dc`).
The new CUDA SHA-256 is
`721e39685cc4f217b6e15a32dc0359cbcd0d2cee671da8fab3b6dd5aa536ee89`.
The complete six-shape three-arm campaign took 15.0116 seconds.

Fixed-capacity measurements where one side processes 4096 rows while the
other
processes only `T < 4096` rows are excluded: unequal work is not kernel
speedup.

## 🔍 Related Issues

Related to #4727.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request,
please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I have installed the hooks.
- [x] Final-commit pre-commit checks pass.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Host tests cover workspace ownership, compatibility, and
lifecycle.
- [x] The B200 benchmark validates both reducers against the ordered
BF16
  reference before timing the matched-work cases.
- [x] BF16 correctness uses `atol=1e-2`, `rtol=1e-2`.
- [x] Four-rank end-to-end validation passes across all six target
shapes,
  alternating profiles, graph replay, and input mutation.
- [x] Compute Sanitizer synccheck: four-rank end-to-end test passes with
zero errors.
- [x] Compute Sanitizer racecheck: delivered native reducer passes all
six shapes,
large-capacity tail checks, and direct/CUDA Graph replay with zero
hazards.
- [x] SASS inspection shows vectorized loads/stores and no local-memory
traffic.
- [x] The authorized GitHub PR test matrix passes for the final commit.

Final validated commit: `e25ba0aac546ef1c3f92c2ebe4eb709b2921891e`.
All 14 jobs in the [authorized test
matrix](https://github.com/flashinfer-ai/flashinfer/actions/runs/34660783619)
pass, including AOT imports on x64/arm64 with CUDA 12.9/13.0 and JIT
tests on A10G, T4, and H100.

[Pre-commit](https://github.com/flashinfer-ai/flashinfer/actions/runs/34660740771),
[API
checks](https://github.com/flashinfer-ai/flashinfer/actions/runs/34660740598),
and [documentation
build](https://github.com/flashinfer-ai/flashinfer/actions/runs/34660740670)
also pass.

## Reviewer Notes

Please focus on the explicit workspace ownership/lifetime contract and
the
strict matched-work benchmark methodology.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added reusable MegaMoE workspaces with capacity-specific profiles and
explicit output-view options.
  * Added a native top-k reduction path for compatible Blackwell GPUs.
* Added public APIs to create, load, and run the optimized reduction
capability.
* **Bug Fixes**
* Improved workspace validation, lifecycle management, cleanup, and CUDA
graph capture safeguards.
* **Documentation**
* Documented workspace creation, lifetimes, ownership, pooling, and
cleanup requirements.
* **Tests**
* Added coverage for multi-rank reduction, workspace reuse, graph
capture, and validation failures.
* **Performance**
  * Added matched and fixed-capacity benchmark comparisons.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4383
- **最后更新**: 2026-09-12T23:49:42Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: lpc0220

## AI分析总结

# FastVideo 昨日提交分析（aef4e9b）

## 1. 主要更新类型
- **功能修复 + 构建/编译优化**：针对 VSA（Video Sparse Attention）kernel 的架构编译策略与反向传播门控进行调整。
- 属于底层 kernel 层面的工程性修复，而非用户可见的新功能。

## 2. 关键变更点
- **每个列出架构生成独立的 sm_100a / sm_103a 镜像**：此前可能将多个架构合并编译，现改为按架构分别产出镜像，避免跨架构兼容性问题。
- **解除 sm_103a 上反向传播的门控限制**：sm_103a（Blackwell 系列新架构）此前被禁止执行 backward，本次放开，意味着该架构可完整支持训练/反向流程。
- 由 Claude Fable 5.1 协作完成，体现 AI 辅助开发在底层 kernel 工作中的参与。

## 3. 对项目的影响与潜在意义
- **提升硬件覆盖完整性**：sm_103a 用户（如最新 Blackwell GPU）现在可运行包含反向传播的完整流程，而不仅是推理。
- **增强编译可靠性**：按架构独立出镜像可减少因架构差异导致的运行时错误或性能退化。
- **支撑训练场景**：FastVideo 作为视频生成加速框架，反向传播可用性直接关系到微调与训练能力，此改动扩展了可训练硬件范围。

## 4. 值得关注的技术点
- sm_100a 与 sm_103a 属于 NVIDIA Blackwell 架构的细分目标（数据中心 vs 消费/新变体），分别出镜像说明项目在紧跟新硬件。
- “un-gate backward”暗示此前存在人为限制，可能是等待验证或编译器支持；解除门控意味着该路径已通过验证。
- VSA kernel 是 FastVideo 的核心加速组件，其架构适配直接影响端到端性能。

## 5. 结合项目背景的发展意义
FastVideo 定位为高效的视频生成推理/训练框架，README 强调快速上手与推理加速。本次提交虽小，但属于**底层硬件适配的持续打磨**：一方面让最新 GPU 架构能完整参与训练流程，另一方面通过精细化编译策略保障跨架构稳定性。这与项目“在多样硬件上提供高性能视频生成”的整体方向一致，为后续在新架构上开展训练与微调扫清了障碍，也反映出项目对 kernel 级优化的持续投入。

## 详细提交记录

### [aef4e9b](https://github.com/hao-ai-lab/FastVideo/commit/aef4e9b3b1423be9d5e39ca463fb085b85c221f6)

- **作者**: lpc0220
- **时间**: 2026-09-12T23:49:36Z
- **提交信息**: [kernel] VSA kernel: one sm_100a / sm_103a image per listed arch; un-gate backward on sm_103a (#1833)


Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34502
- **最后更新**: 2026-09-12T20:52:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
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


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13089
- **最后更新**: 2026-09-12T14:03:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35862
- **最后更新**: 2026-09-12T23:58:24Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 18
- **主要提交者**: Yanbin Jiang, Xiaoyu Zhang, Byron Hsu

## AI分析总结

# sglang 昨日提交分析总结

## 1. 主要更新类型

本批 22 条提交覆盖了**功能新增、Bug 修复、性能优化、文档更新、重构**五大类，且高度集中在以下几个方向：

- **MoE / 量化支持**：ROCm 统一 Triton router、GraniteMoE 分专家量化权重加载、MiniMax-M3 MXFP4 修复。
- **AMD/ROCm 生态**：多条 AMD 相关修复与文档（GLM-5.2 MXFP4、DSV4、MI355X）。
- **图执行与内存优化**：graph-pool 借用作用域、CUDA graph 去重复用、Unified Tree 相关重构。
- **新模型/新能力**：Mamba 2 与 Mamba 1 推理支持、Qwen3-VL 性能优化、Responses API 扩展。
- **diffusion 子系统**：注意力后端自动测量选择、host 无法缓存时直接读取映射层。

## 2. 关键变更点与项目方向的关系

- **MoE 与量化是核心主线**：ROCm 上统一 Triton router 的引入，意味着 SGLang 正在收敛跨硬件（NVIDIA/AMD）的 MoE 路由实现，减少平台分叉。GraniteMoE 分专家量化权重加载则强化了对异构量化模型的支持。
- **AMD 生态持续加码**：从文档（GLM-5.2 MXFP4 recipe）到修复（Dspark accept length、Quark 加载），显示 AMD 已成为与 NVIDIA 并列的一等公民。
- **图执行与内存管理精细化**：graph-pool 借用作用域收敛、CUDA graph 去重注册复用、Unified Tree 的 LRU 与 SWA 分支缓存移植，均指向**降低显存碎片、提升长上下文/多请求场景稳定性**。
- **API 与多模态能力扩展**：Responses API 支持自定义工具、加密推理回放、模型校验，配合 Session+MM 文本位置修复，说明项目在向生产级 Agent/多轮会话场景演进。

## 3. 对项目的影响与潜在意义

- **跨硬件一致性提升**：统一 Triton router 降低了 ROCm 与 CUDA 的行为差异，有利于社区贡献与测试复用。
- **显存效率与稳定性改善**：graph-pool 与 CUDA graph 优化直接缓解长序列、高并发下的碎片与 OOM 风险，对推理服务 SLA 有实际价值。
- **模型覆盖面扩大**：Mamba 2/1 支持、GraniteMoE、Qwen3-VL 优化，使 SGLang 能覆盖更多主流与新兴架构。
- **生产可用性增强**：Responses API 的加密推理回放与工具支持，是面向企业级 Agent 部署的重要铺垫。

## 4. 值得关注的技术点

- **统一 Triton router 在 ROCm 上的单组路由**：跨平台 MoE 路由收敛的关键一步。
- **graph-pool 借用作用域限定**：从全局借用改为运行时作用域，是显存碎片治理的架构级改动。
- **CUDA graph 去重时复用活跃 executable**：避免重复注册带来的开销与内存浪费。
- **diffusion 注意力后端按测量选择**：从静态配置转向运行时自适应，提升不同硬件下的鲁棒性。
- **Unified Tree 的 Rust TreeCore 移植**：SWA 分支点缓存与 LRU 保持，暗示 KV cache 树结构正在向 Rust 侧迁移以提升性能。

## 5. 基于项目背景的发展影响

SGLang 定位为**高性能 LLM 与多模态推理服务框架**，强调吞吐、低延迟与广泛模型/硬件支持。本批提交延续了这一方向：

- 通过 MoE/量化与 AMD 支持，**扩大硬件与模型覆盖面**，巩固其在开源推理框架中的竞争力。
- 通过图执行与显存优化，**持续压低推理成本**，这是服务框架的核心价值主张。
- 通过 Responses API 与多模态修复，**向 Agent 与生产部署场景延伸**，从纯推理引擎向完整服务栈演进。

整体看，这是一批**以工程稳健性和跨平台一致性为主、兼顾新模型与新 API 能力**的提交，符合 SGLang 从“快”向“快且稳、广且生产可用”发展的整体节奏。

## 详细提交记录

### [6657f7d](https://github.com/sgl-project/sglang/commit/6657f7d8449f7c739906b6f8ebcb016dddcbceef)

- **作者**: xiaobochen-amd
- **时间**: 2026-09-12T23:21:28Z
- **提交信息**: [MoE][ROCm] Admit the unified Triton router on ROCm, including single-group routing (#38328)

Co-authored-by: JohnQinAMD <yanyuan.qin@amd.com>
Co-authored-by: RuibinCheung <ruibzhan@amd.com>
Co-authored-by: Zhang, Jiejing <jiejing.zhang@amd.com>

### [a66451c](https://github.com/sgl-project/sglang/commit/a66451c058dcce0799f5c6d1620b527371db4828)

- **作者**: Baizhou Zhang
- **时间**: 2026-09-12T23:01:11Z
- **提交信息**: [GLM-5.3 Flash] Restore and enable KPool metadata fusion (#38845)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: zRzRzRzRzRzRzR <Yuxuan.Zhang2@liverpool.ac.uk>
Co-authored-by: Shijin Zhang <75300765+Dovis01@users.noreply.github.com>
Co-authored-by: zanes-ops <zanes@nvidia.com>

### [288627e](https://github.com/sgl-project/sglang/commit/288627e4006ab455058621e232e3eedcf1e8bb03)

- **作者**: Zhang, Jiejing
- **时间**: 2026-09-12T22:57:15Z
- **提交信息**: [AMD] Document GLM-5.2 MXFP4 recipe update on MI355X (#39230)

### [21289cf](https://github.com/sgl-project/sglang/commit/21289cfd50a8cf7550c1786ac71733bec9396d4d)

- **作者**: Xinyi Song
- **时间**: 2026-09-12T22:21:43Z
- **提交信息**: [AMD] Fix Dspark accept length and reduce host bubble on DSV4 (#39116)

### [b5a2aeb](https://github.com/sgl-project/sglang/commit/b5a2aebc7eccd4ee0afa8c435585d7462d7d7a61)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-12T19:56:57Z
- **提交信息**: [Docs] GLM-5.3-Flash cookbook: fixed MTP 5/1/6, EP1 + flashinfer_trtllm on Blackwell (#39213)

### [7ae4af8](https://github.com/sgl-project/sglang/commit/7ae4af8187cbe9740a90f66ee5c09e38f0bb0a3c)

- **作者**: cctry
- **时间**: 2026-09-12T18:45:17Z
- **提交信息**: Scope graph-pool borrowing to the runtime and reduce fragmentation (#39177)

Co-authored-by: cctry <17473714+cctry@users.noreply.github.com>

### [2784a86](https://github.com/sgl-project/sglang/commit/2784a860621f73e90d871b26ab3eca801bc4e142)

- **作者**: cctry
- **时间**: 2026-09-12T18:44:17Z
- **提交信息**: Reuse live CUDA graph executables during dedup registration (#39176)

Co-authored-by: cctry <17473714+cctry@users.noreply.github.com>

### [25a5641](https://github.com/sgl-project/sglang/commit/25a5641cf290eeba0c1cc9ca0660447f0482d432)

- **作者**: Byron Hsu
- **时间**: 2026-09-12T17:31:55Z
- **提交信息**: [Session + MM] Fix text positions in session continuations (#39144)

Co-authored-by: Byron Hsu <byron+per@periodiclabs.ai>
Co-authored-by: Manik Singhal <3400497+Manikvsin@users.noreply.github.com>

### [ae1acf8](https://github.com/sgl-project/sglang/commit/ae1acf822dd357641d885f30c58d2ad547ec9220)

- **作者**: jlqibm
- **时间**: 2026-09-12T15:10:20Z
- **提交信息**: [GraniteMoE] Load split per-expert quantized MoE weights (#37679)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [7b89b95](https://github.com/sgl-project/sglang/commit/7b89b95168aad38266207fc442ea50b0d15aed7d)

- **作者**: Mick
- **时间**: 2026-09-12T13:52:16Z
- **提交信息**: [diffusion] feat: pick the attention backend by measuring it (#38689)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [dc3171c](https://github.com/sgl-project/sglang/commit/dc3171c32291b885d7699af1f770c9fc1642f9e0)

- **作者**: Mick
- **时间**: 2026-09-12T13:48:04Z
- **提交信息**: [diffusion] CI: remove mova ulysses two-gpu CI case (#39097)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [925e684](https://github.com/sgl-project/sglang/commit/925e684a88f511bed77f7c0ce3c74fb0907b3ef9)

- **作者**: Shijin Zhang
- **时间**: 2026-09-12T13:29:12Z
- **提交信息**:  [Feat][Responses API] Support custom tools, encrypted reasoning replay, developer tier and model validation (#38690)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [6dc7b34](https://github.com/sgl-project/sglang/commit/6dc7b3421b48ab962e9567cb3a595fcb7bfe1e00)

- **作者**: desmond-intel
- **时间**: 2026-09-12T12:51:18Z
- **提交信息**: Inference Support Mamba 2 and 1 (#34556)

### [fd32226](https://github.com/sgl-project/sglang/commit/fd3222670660cc31b70972bfd145631d6bf0932b)

- **作者**: Kunal
- **时间**: 2026-09-12T12:21:59Z
- **提交信息**: Fix gpt-oss RunAI streamer weight ownership (#38908)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [bd45cd5](https://github.com/sgl-project/sglang/commit/bd45cd50ca900dd821f829ca9adfbf9aa3336bda)

- **作者**: Shuwen Wang
- **时间**: 2026-09-12T10:37:57Z
- **提交信息**: [Unified Tree] Port SWA Branching-Point Caching to the Rust TreeCore (#37584)

### [0b415fa](https://github.com/sgl-project/sglang/commit/0b415fa57312337903478ed30e00ab3ab714548e)

- **作者**: Yanbin Jiang
- **时间**: 2026-09-12T10:18:14Z
- **提交信息**: [HiCache][LoRA] Isolate storage pages by extra key (#38577)

Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [b9cb964](https://github.com/sgl-project/sglang/commit/b9cb96496dcd2f0c6c4dce72fe2672dc56aaf1e8)

- **作者**: Shuwen Wang
- **时间**: 2026-09-12T10:17:38Z
- **提交信息**: [Unified Tree] Preserve aux LRU recency when splitting nodes (#38482)

### [6953dae](https://github.com/sgl-project/sglang/commit/6953dae0057b197cad4b665bba6692d2ce02516c)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-12T08:32:01Z
- **提交信息**: [Qwen 3.8 Next] Remove unused tokenwise QSA implementation and tests (#38960)

### [7bc4eb3](https://github.com/sgl-project/sglang/commit/7bc4eb3740330630c0af56b3ad9cd2ecb3dcdbb8)

- **作者**: ChangLiu0709
- **时间**: 2026-09-12T07:59:32Z
- **提交信息**: [AMD] Update MI355X MXFP4 HiCache defaults and quick-reduce quantization for Qwen3.5 cookbook (#39104)

### [7c195b9](https://github.com/sgl-project/sglang/commit/7c195b9151627320b2a4688251adc12975712a86)

- **作者**: Tuan Nguyen Gia
- **时间**: 2026-09-12T07:50:41Z
- **提交信息**: [AMD] Fix Quark load of MiniMax-M3 MXFP4 index_qkv_proj (#37254)

### [bf3305b](https://github.com/sgl-project/sglang/commit/bf3305b65e960b803c9a5649099fe48d85e8a94c)

- **作者**: Mick
- **时间**: 2026-09-12T07:48:03Z
- **提交信息**: [diffusion] feat: read mapped layers directly when the host cannot cache them (#39022)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [0a57403](https://github.com/sgl-project/sglang/commit/0a574034680b97e4867acb6ee8cab5f84ffac154)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-12T07:16:59Z
- **提交信息**: [Perf] Optimize Qwen3-VL unique-image serving on H100 (#36411)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1275
- **最后更新**: 2026-09-10T02:30:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91594
- **最后更新**: 2026-09-12T23:48:33Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 22
- **主要提交者**: PatrykSaffer, Zeyu Yang, Nicolò Lucchesi

## AI分析总结

# vLLM 昨日提交分析总结（共26条）

## 1. 主要更新类型分布

- **功能新增/扩展**：HiSparse 缓存跨 TP 共享（#5/N）、PCP+DCP 稀疏 MLA 支持、双密钥 Gumbel-max 水印、统一 Cohere 解析器、Elastic EP CUDA 图复用。
- **Bug 修复**：ROCm 弹性 EP 死锁、DeepGEMM FP8 预热覆盖、Nano-Nemotron 多模态嵌入、CuTeDSL 索引器测试、Rust 前端空结构化输出拒绝。
- **性能优化**：DSV4.1 输入元数据 Triton 融合、Elastic EP 重配置复用 CUDA 图。
- **CI/构建**：多条 CI 修复与增强（GPU 利用率采样、Torch ABI 审计、XPU/ROCm 平台隔离、DSv4.1 自动标签）。
- **重构**：ROCm RDNA3 W4A16 MoE 迁移至 oracle/experts 路径。

## 2. 关键变更点与项目方向

- **稀疏注意力与缓存体系持续深化**：HiSparse 主机缓存跨 TP 共享（#5/N）及缓存指标暴露（#4/N），配合 PCP+DCP 稀疏 MLA 支持，表明 vLLM 正系统性地完善大规模稀疏模型（如 DeepSeek 系列）的分布式推理能力。
- **Elastic EP 成熟化**：从修复死锁到复用 CUDA 图，弹性专家并行正从可用走向高效，契合"cheap serving"目标。
- **DSV4.1 专项优化密集**：元数据融合、路由测试更新、图像哨兵 token 移除，显示对最新旗舰模型的一等公民支持。
- **前端与生态扩展**：Rust 前端健壮性、Cohere 统一解析器，强化多后端与多厂商兼容。

## 3. 对项目的影响与潜在意义

- 跨 TP 缓存共享与 PCP+DCP 支持直接提升超长上下文、大规模并行场景下的显存效率与吞吐，是 vLLM 服务超大规模模型的关键基础设施。
- Elastic EP 的 CUDA 图复用显著降低重配置开销，对动态扩缩容的生产部署意义重大。
- 大量 CI 修复与增强（GPU 采样、平台隔离、自动标签）提升开发迭代速度与回归防护，保障快速演进中的稳定性。
- 水印功能支持投机解码，兼顾合规与性能，拓展企业级应用场景。

## 4. 值得关注的技术点

- **HiSparse 主机缓存跨 TP 共享**：涉及分布式缓存一致性与 KV 连接器统计，是稀疏注意力工程化的核心难点。
- **双密钥 Gumbel-max 水印 + 投机解码**：在加速解码的同时保持可验证水印，算法与系统协同设计。
- **Elastic EP CUDA 图跨重配置复用**：解决动态并行下的图捕获难题，技术门槛高。
- **DSV4.1 Triton 元数据融合**：以 kernel 融合降低 CPU 开销，体现端到端性能打磨。

## 5. 结合 README 的项目发展影响

README 定位 vLLM 为"Easy, fast, and cheap LLM serving for everyone"。本批提交从三个维度推进该目标：**fast**——Triton 融合、CUDA 图复用、稀疏缓存共享持续压低延迟与显存；**cheap**——弹性 EP 与跨 TP 缓存共享降低多卡部署成本；**easy**——统一 Cohere 解析器、Rust 前端健壮性、CI 自动化降低使用与贡献门槛。同时，对 DeepSeek V4.1、Nano-Nemotron 等前沿模型的密集适配，确保 vLLM 始终是新一代模型的首选服务框架，巩固其作为开源 LLM 推理事实标准的生态地位。

## 详细提交记录

### [e19a3e1](https://github.com/vllm-project/vllm/commit/e19a3e172ecc1d1ece8ecce9dfd91bf811a814a0)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-12T23:48:25Z
- **提交信息**: [5/N] Share HiSparse host cache across TP ranks (reopens #52760) (#56629)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Signed-off-by: Chao Lei <leichao139636@163.com>
Signed-off-by: Lucas Wilkinson <lwilkinson@neuralmagic.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Chao Lei <leichao139636@163.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [ebe1dec](https://github.com/vllm-project/vllm/commit/ebe1dec2da16ac559e40446a4c6e06a73c9efe00)

- **作者**: PatrykSaffer
- **时间**: 2026-09-12T23:24:44Z
- **提交信息**: [PCP][DCP] Enable PCP+DCP on sparse-MLA models (#56157)

Signed-off-by: patryk.saffer <patryk.saffer@blc-login-1.blc1.mistralcompute.ai>
Signed-off-by: patryk.saffer <patryk.saffer@blc-login-0.blc1.mistralcompute.ai>
Signed-off-by: PatrykSaffer <patryk.saffer@mistral.ai>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: patryk.saffer <patryk.saffer@blc-login-1.blc1.mistralcompute.ai>
Co-authored-by: patryk.saffer <patryk.saffer@blc-login-0.blc1.mistralcompute.ai>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Patryk Saffer <PatrykSaffer@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [72d4d83](https://github.com/vllm-project/vllm/commit/72d4d8315749c146cf19f047fecfec491911770d)

- **作者**: Matt
- **时间**: 2026-09-12T23:09:19Z
- **提交信息**: [ROCm][Bugfix] Fix elastic EP scaling deadlock (#56610)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [7ee8a6d](https://github.com/vllm-project/vllm/commit/7ee8a6dd013819838da8012ca549d724bee7c6c6)

- **作者**: Raphaël Rialland
- **时间**: 2026-09-12T18:42:01Z
- **提交信息**: [watermarking] Dual-key gumbel-max watermarking for speculative decoding support (#56122)

Signed-off-by: Raphael Rialland <raphael.rialland@mistral.ai>
Signed-off-by: Simon Veitner <sveitner@redhat.com>
Signed-off-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>

### [1ee4be4](https://github.com/vllm-project/vllm/commit/1ee4be4dbc576f2158913a89598ccfa9dec9391e)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-12T18:31:13Z
- **提交信息**: [CI] Update DeepSeek V4.1 MegaMoE routing test (#56599)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [fd7cd4b](https://github.com/vllm-project/vllm/commit/fd7cd4b883e7720fbbfbc0ca6aa9404bf2f8e3f1)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-12T18:29:58Z
- **提交信息**: [CI] Fix Qwen3 Omni DSpark load test config (#56600)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [7bcca16](https://github.com/vllm-project/vllm/commit/7bcca16729b71294bd1b67ecde9aca584618234d)

- **作者**: Ayushman Singh
- **时间**: 2026-09-12T18:20:38Z
- **提交信息**: [Bugfix] Fix DeepGEMM FP8 warmup coverage (#56452)

Signed-off-by: Ayushman Singh <40520701+ayush1399@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [29332cf](https://github.com/vllm-project/vllm/commit/29332cf93628a67c49252ef7c89a8aa3185def4b)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-12T17:47:55Z
- **提交信息**: [4/N] Expose HiSparse cache metrics via KV connector stats (#56061)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [dff76bc](https://github.com/vllm-project/vllm/commit/dff76bc3e8d702901e6dda5971f9506a6c1bc00f)

- **作者**: Zeyu Yang
- **时间**: 2026-09-12T17:03:28Z
- **提交信息**: [Bugfix][CI] skip conftest for NPU compatibility test (#55799)

Signed-off-by: yangzeyu <532183776@qq.com>

### [3bb23e2](https://github.com/vllm-project/vllm/commit/3bb23e2def9527d941be57c5a7d47401a8dbaedc)

- **作者**: jcotant-inferact
- **时间**: 2026-09-12T16:50:16Z
- **提交信息**: [CI/Build] Add DSv4.1 auto-label rules and narrow DSv4 (#56332)

Signed-off-by: Joe Cotant <joe@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>

### [9d3e991](https://github.com/vllm-project/vllm/commit/9d3e991ece7f54c173c0cc9261ab5969b1dbeb4c)

- **作者**: Artem Perevedentsev
- **时间**: 2026-09-12T16:32:12Z
- **提交信息**: Add @arpera to CODEOWNERS of Structured Output (#56501)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [c377114](https://github.com/vllm-project/vllm/commit/c377114636db645e13594e66a6c4f4f0084adac2)

- **作者**: Roberto L. Castro
- **时间**: 2026-09-12T16:12:58Z
- **提交信息**: [Bugfix][CI] Update CuTeDSL indexer Q sentinel test for migrated wrappers (#56594)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>

### [22f6e4e](https://github.com/vllm-project/vllm/commit/22f6e4eccb674b534f62810c66838317169b6b98)

- **作者**: Clinton Thomas
- **时间**: 2026-09-12T15:12:25Z
- **提交信息**: [Frontend][Rust] Reject empty structured-output values (#54821)

Signed-off-by: Clinton Thomas <1033162+KernelClint@users.noreply.github.com>
Co-authored-by: Lucas Bourtoule <35483370+dhalf@users.noreply.github.com>

### [658c813](https://github.com/vllm-project/vllm/commit/658c8131c73194f812cd80d493e0409475b94235)

- **作者**: Itay Alroy
- **时间**: 2026-09-12T14:26:39Z
- **提交信息**: [Elastic EP] Reuse CUDA graphs across reconfiguration (#54985)

### [13e221f](https://github.com/vllm-project/vllm/commit/13e221f8308416564a446909c2fd4805c78fbb8a)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-12T14:20:04Z
- **提交信息**: [Perf] Fuse DSV4.1 input metadata preparation with Triton (#56562)

### [2f59050](https://github.com/vllm-project/vllm/commit/2f59050eda23bccf530dbe924ce4877b25a031cc)

- **作者**: liuzhenwei
- **时间**: 2026-09-12T13:26:55Z
- **提交信息**: [XPU][CI] Skip ROCm test on non-ROCm platforms (#56555)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [986e2f8](https://github.com/vllm-project/vllm/commit/986e2f870abc8f87a1830af7d335961b3e4234b2)

- **作者**: JartX
- **时间**: 2026-09-12T13:20:26Z
- **提交信息**: [Refactor][ROCm] Migrate the RDNA3 W4A16 MoE to the oracle/experts pa… (#55522)

Signed-off-by: JartX <sagformas@epdcenter.es>

### [1b29c50](https://github.com/vllm-project/vllm/commit/1b29c508bcb25fbfd9ab4c3d61ae131d7e0700d5)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-12T13:07:20Z
- **提交信息**: [Bugfix] Initialize data parser in Nano-Nemotron audio test (#56401)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [a0914ab](https://github.com/vllm-project/vllm/commit/a0914ab7d07b9a788db15b499edf3b5a280e7a14)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-12T13:07:10Z
- **提交信息**: [Nano-Nemotron] Fix Nano-Nemotron precomputed multimodal embeddings (#56398)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [bde4feb](https://github.com/vllm-project/vllm/commit/bde4feb06123d5bdefbf817b840e3489113548c5)

- **作者**: Kunshang Ji
- **时间**: 2026-09-12T12:03:12Z
- **提交信息**: [XPU][CI] Remove pip install dependency in test yaml files (#55171)

Signed-off-by: Kunshang Ji <jikunshang95@gmail.com>

### [d86257e](https://github.com/vllm-project/vllm/commit/d86257e2833e0c3add2c694a380435c451c1b176)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-12T10:29:22Z
- **提交信息**: [CI/Build] Give the Torch ABI audit time to start (#56596)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [6b15346](https://github.com/vllm-project/vllm/commit/6b153463a8a6721fd4bb89ec9afa014409bcce36)

- **作者**: Srijan Keshri
- **时间**: 2026-09-12T09:45:32Z
- **提交信息**: [Build] Define _USE_MATH_DEFINES for FlashMLA targets (#54007)

Signed-off-by: arcusbuilds <srijankeshri007@gmail.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [33fa95a](https://github.com/vllm-project/vllm/commit/33fa95a0cf9ed6bf384a0a51667a01a4f0bb02d5)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-12T09:41:54Z
- **提交信息**: [CI] Sample GPU utilization and memory alongside test timelines (#56541)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [756794a](https://github.com/vllm-project/vllm/commit/756794a9a7f08900c00fbfaa6d8332631503f528)

- **作者**: Walter Beller-Morales
- **时间**: 2026-09-12T08:04:46Z
- **提交信息**: [Frontend] create unified Cohere parser (#56392)

Signed-off-by: walterbm <walter.beller.morales@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [d406f09](https://github.com/vllm-project/vllm/commit/d406f09eb8d05eaf81d768bf74212bc6d24cd11d)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-12T07:40:14Z
- **提交信息**: [ROCm][CI] Stage F gating (#55252)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [30118ba](https://github.com/vllm-project/vllm/commit/30118ba27d1d923bdd91f97d945528dcb4a862c1)

- **作者**: Isotr0py
- **时间**: 2026-09-12T07:07:36Z
- **提交信息**: [DSV4.1] Remove compressor-aware image sentinel token padding (#56554)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-13
**监控日期**: 2026-09-12
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6776
- **最后更新**: 2026-09-12T16:45:04Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: geray, Anjie Hou, Alicia

## AI分析总结

# vllm-omni 昨日提交分析（3 条）

## 1. 主要更新类型

- **性能优化**：视频流式编码的有界批处理（#7018）、CosyVoice3 Stage1 流批处理优化（#4876）。
- **重构**：从 LoRA 与 ModelOpt 加载器默认值中移除模型专属命名（#5907）。
- 整体偏向**推理效率与代码通用性**，而非新功能或文档。

## 2. 关键变更点与项目方向

- **#7018（[3/N] 流式视频编码）**：将视频编码放到 worker 端执行，并引入“有界批处理”（bounded batching）。这是系列补丁的第 3 部分，说明团队正系统性地把多模态预处理/编码下沉到 worker，配合 vLLM 的分布式执行架构，避免中心节点瓶颈。
- **#4876（CosyVoice3 Stage1 批处理优化）**：针对语音合成模型的 Stage1 流程做批处理优化，直接提升 TTS 类 omni 模型的吞吐。
- **#5907（LoRA/ModelOpt 加载器重构）**：去掉默认值中的模型专属名称，使加载器更通用、可扩展，符合“面向所有人的 omni 多模态服务”的通用化目标。

三者共同指向 README 所述“Easy, fast, and cheap”的定位：**更快（批处理/worker 编码）、更通用（去模型耦合）**。

## 3. 对项目的影响与潜在意义

- 视频与语音两条多模态链路同时获得吞吐优化，说明项目在**音频+视频**方向并行推进，而非单点突破。
- 有界批处理意味着在延迟与显存之间做平衡，是生产级 serving 的关键工程手段，有助于降低单位推理成本（对应“cheap”）。
- 加载器去模型化降低了新增模型（LoRA、量化）的接入成本，利于生态扩展与社区贡献。

## 4. 值得关注的技术点

- **有界批处理（bounded batching）**：如何在流式场景下控制批大小上限，兼顾吞吐与首帧延迟。
- **worker 端编码**：编码任务从调度侧迁移到 worker，涉及数据搬运、序列化与负载均衡。
- **CosyVoice3 Stage1 流批处理**：语音合成中流式与批处理的结合方式。
- **LoRA/ModelOpt 默认值解耦**：重构后默认行为是否变化、是否影响向后兼容，需关注迁移说明。

## 5. 结合项目背景的发展影响

vllm-omni 目标是“面向所有人的 omni 多模态模型服务”。本次提交没有引入新模型，而是**打磨现有链路的效率与通用性**：视频编码下沉 worker、语音批处理优化、加载器去耦合，都是把原型能力推向生产可用的关键步骤。这表明项目正从“支持多模态”走向“高效、可扩展地服务多模态”，为后续接入更多模型和更大规模部署打基础。整体方向健康，属于典型的性能与架构演进阶段。

## 详细提交记录

### [7e520f9](https://github.com/vllm-project/vllm-omni/commit/7e520f9cc47e6884520ea8f3f9ab94ab97b34780)

- **作者**: Anjie Hou
- **时间**: 2026-09-12T12:58:11Z
- **提交信息**: [3/N] Encode streamed video on the worker with bounded batching (#7018)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [9edc1b4](https://github.com/vllm-project/vllm-omni/commit/9edc1b4667d4b56d12effe1e5b300315520d1ae3)

- **作者**: geray
- **时间**: 2026-09-12T12:31:49Z
- **提交信息**: Optimize CosyVoice3 Stage1 flow batching (#4876)

Signed-off-by: gerayking <399geray@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [28291df](https://github.com/vllm-project/vllm-omni/commit/28291df1795129ae03ce86a7b9b0a230166b5ac5)

- **作者**: Alicia
- **时间**: 2026-09-12T12:30:03Z
- **提交信息**: [Refactor][Diffusion] Remove model-specific names from LoRA and ModelOpt loader defaults (#5907)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
