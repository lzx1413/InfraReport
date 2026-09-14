# GitHub Stars 合并报告 - 2026-09-13

**合并日期**: 2026-09-14
**监控日期**: 2026-09-13
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


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2207
- **最后更新**: 2026-09-13T10:16:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2807
- **最后更新**: 2026-09-13T16:38:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
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


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6397
- **最后更新**: 2026-09-13T21:53:22Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Shanli Xing, eigen

## AI分析总结

## 一、主要更新类型

本批次共 2 个提交，均为**性能优化与功能新增**，无 Bug 修复或文档更新：

- **e500442**：`perf(cake_comm)` —— 针对 SM120 架构的 PCIe CE ring 发布开销优化。
- **93e9eef**：`feat(cake_alpha_moe)` —— 新增 Blackwell W8A8 专家 up/down 计算算子。

## 二、关键变更点与项目方向

1. **SM120 专用通信路径**：仅在参与 rank 全部为 SM120（compute capability 12.0）、TP4/TP8 且 piece count 为 1 时启用流发布优化；其他架构完全保留原协议与回退路径，不分配额外二进制就绪区、不做额外能力 all-gather。这体现了 FlashInfer 在保持跨架构兼容的前提下，对特定新硬件做**运行时特化**的策略。

2. **Blackwell W8A8 MoE 算子**：新增专家 up/down 计算，优化输出调度与 scale 复用，并对齐参考 scale 舍入。这直接服务于低精度（W8A8）MoE 推理场景。

两者均指向项目核心目标——**为推理提供高性能 GPU kernel**，且明显向 Blackwell（SM120/B200/B300）等新架构倾斜。

## 三、对项目的影响与潜在意义

- **架构分层优化**：SM120 特化说明项目开始针对不同 GPU 代际做差异化调优，而非“一刀切”，有利于在新硬件上榨取性能，同时不牺牲旧架构稳定性。
- **量化推理能力增强**：W8A8 MoE 算子补齐了 Blackwell 上低精度专家计算的空白，对大规模 MoE 模型部署有直接价值。
- **性能声明审慎**：提交中明确区分“非 SM120 设备上的近中性测量”与“SM120 专项对比”，并主动指出 B300 某行 5.33% 延迟上升原因未明，体现了对性能结论的严谨态度。

## 四、值得关注的技术点

- **运行时特化 vs 编译期裁剪**：作者强调这是运行时特化，共享 ring 与可链接 leaf 仍为公共源码，非整 PR 编译排除。
- **能力传播机制**：group capability 通过既有 preparation exchange 传递，避免新增通信开销。
- **性能数据解读**：五类非 SM120 GPU 均值接近持平，SM120 专项报告 1.020× 平均延迟比、TP4 FP16 12MiB 下达 1.159×，但作者明确表示“正确性与 CI 通过不等于性能验收通过”。
- **W8A8 scale 复用与舍入对齐**：涉及数值精度一致性，是量化算子正确性的关键细节。

## 五、结合 README 背景的项目发展影响

FlashInfer 定位为“High-Performance GPU Kernels for Inference”，本批次提交延续其**面向新硬件、面向低精度推理**的演进路线：一方面通过 SM120 通信特化降低 PCIe 开销，另一方面通过 Blackwell W8A8 MoE 算子扩展量化推理覆盖。两者共同强化了项目在 Blackwell 世代上的竞争力，同时以保守的回退设计维护了跨架构可用性，符合其作为通用高性能推理 kernel 库的定位。

## 详细提交记录

### [e500442](https://github.com/flashinfer-ai/flashinfer/commit/e500442f83fe9aac7969eb1c8731b6921fa6f180)

- **作者**: eigen
- **时间**: 2026-09-13T17:58:37Z
- **提交信息**: perf(cake_comm): reduce PCIe CE ring publication overhead on SM120 (#5169)

| GPU | Baseline mean (ms) | Candidate mean (ms) | Speedup |
|---|---:|---:|---:|
| H100 | 0.267771 | 0.268482 | 0.997351× |
| GB200 | 0.143053 | 0.143131 | 0.999452× |
| GB300 | 0.145567 | 0.145749 | 0.998749× |
| B200 | 0.171413 | 0.170973 | 1.002574× |
| B300 | 0.163397 | 0.162827 | 1.003499× |

**SM120-only specialization:** Stream publication is enabled only when
every participating rank is SM120 (compute capability **12.0**), the
group is TP4/TP8, and the resolved piece count is one. Other
architectures keep the original protocol and fallback. Non-SM120 devices
now also keep the original workspace extent/zeroing and v3 tuning-cache
identity: they allocate no binary readiness region, perform no extra
capability all-gather, and make no memop enable/launch-state update.
Group capability travels in the existing preparation exchange. The
shared ring and linkable leaf remain common source; this is runtime
specialization, not a claim that the entire PR is compiled out on other
targets.

**Reading the table:** All five GPU families above are non-SM120
devices. These measurements assess the existing paths after the
refactor; they do not demonstrate a general cross-architecture speedup.
Family means are near parity. The worst B300 row (TP4 BF16, 48 MiB)
records **0.949393×**, or **5.33% higher latency**; its cause is
unresolved, and the two paired rounds do not establish that it is
measurement noise. A claim of performance neutrality needs further
qualification of that row. The separate qualified SM120 comparison
reports **1.020006×** ratio of mean latencies (1.772696 → 1.737927 ms),
with **1.15905×** on TP4 FP16 12 MiB. Correctness and CI passes are
distinct from a performance acceptance decision.

Measured heads remain unchanged: baseline
`d45a83981990767fc171e8cd8da5fef5d617a24e` and candidate
`095abe79c476dd2216cd97074c3810624a02960a`; H100/B200/B300 cover TP4/TP8
and GB200/GB300 cover TP4, with speedup defined as baseline/candidate.

<!-- sm120-resource-isolation -->
**Source follow-up `a85ffbb07e65`:** The resource/admission/cache
isolation is now implemented in code, with regression tests that load
real legacy v3 and SM120 v4 tuning entries and exchange
mixed-capability/failure outcomes across real Gloo ranks. SM120 v4 keys
stay compatible with the previously enabled path.

Fresh checks on this source: **12/12 SM120 GPU tests, zero
skips/failures**, covering TP4/TP8 BF16/FP16 Graph replay, skewed ranks
and mixed-protocol reuse; actual loading of the newly built module
succeeds on all eight CC12.0 devices. Admission is **3/3 passed**;
tuning is **34 passed, 1 pre-existing strict xfail**. All eight
compilation/shared-link targets (SM80/86/89/90a/100a/103a/120a/121a)
pass in **22.850 s**, and the changed-file pre-commit checks pass. The
SM120 GPU pytest interval is **88.684 s**; module/admission/GPU
orchestration totals **120.133 s**. Both embedded SM120 cubins are
byte-identical to the previously qualified device code. Historical
timings below retain their measured source binding and were not rerun
for this host-only change.

Fresh validation of this source on **four GB200 (SM100 / CC10.0) GPUs
passed**: **3 passed, 0 skipped, 0 failed**, covering actual module
loading and TP4 BF16/FP16 original-path/eager/CUDA Graph behavior. All
**64 rank/config records** passed, including explicit memop-request
fallback, changed-input replay, skewed ranks and eager interleaving.
Every device reported `memop_supported=false`. **36/36 workspace-size
comparisons** match the original
`d45a83981990767fc171e8cd8da5fef5d617a24e` baseline exactly (four
devices × TP2/TP4/TP8 size queries × three capacities). TP8 size queries
do not execute collectives; the two TP8 GPU cases were explicitly
deselected on this four-GPU node. The 12 frozen input hashes match
current commit `a85ffbb07e65a64cd857d688391d70073d50ecdf`.

GB200 pytest took **23.89 s** (JUnit interval 23.355 s; subprocess
30.003 s); the in-container runner took **135.677 s**, and the complete
managed step including image import took **343.352 s**. The candidate
workspace/module-build probe took 13.332 s and the subsequent
module-load check 5.572 s. This closes the requested single non-SM120
compatibility check. Historical performance measurements remain bound to
their recorded source; this check does not remeasure performance or
resolve the historical slower B300 row.

Physical turnaround through this final validation/publication checkpoint
is **3616.9 s**, from **2026-09-13 07:35:44 UTC** to **2026-09-13
08:36:01 UTC**, including resource scheduling, preparation and
validation.
<!-- end sm120-resource-isolation -->

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend #4870's existing flat copy-engine ring with an optional
stream-publication strategy for single-piece all-reduce on SM120. The
existing ring loop, packed BF16/FP16 add kernels, and final neighbour
handshake are shared. The only new device leaf waits for binary
readiness with a system-acquire load and clears it; the outgoing copy
publishes readiness with a default-fenced stream write. This removes the
separate per-hop publication kernel and event handoff while preserving
reduction order and scratch reuse.

Variant 4 instantiates the original strategy. Variant 6 uses stream
publication only when every rank agrees on SM120 and the resolved piece
count is one; other groups and deeper pipelines use the shared original
strategy. The CUDA v2 32-bit stream-write API is available by default;
admission does not use the deprecated v1 capability attribute. The
original island schedule remains separate. The tuner considers the new
P1 tactic alongside existing candidates, with capability-aware cache
keys.

There is one ring implementation and one generated device leaf. Compared
with the pre-refactor version, sharing the schedule and device
implementation reduces production code by 375 lines. The generic
wait-and-clear leaf is defined for every build target so its host launch
stub and device definition link correctly on non-SM120 builds; runtime
admission of the optimization remains SM120-only.

On eight PCIe Gen5 x16 CC12.0 GPUs, the complete sixteen-point held-out
comparison reduces arithmetic mean collective latency from **1.772696 to
1.737927 ms (1.020006x)**. Secondary geometric-mean speedup is
**1.039546x**; worst observed speedup is **0.997218x**, on the shared
original TP4 FP16 48 MiB P2 path. TP4 retains P2 at 48/96 MiB; other
selected points use variant 6/P1. These are the previously frozen
selections, measured again after the refactor.

| TP | Type | Payload MiB | Baseline ms | Refactor ms | Speedup |
|---:|---|---:|---:|---:|---:|
| 4 | BF16 | 12 | 0.443664 | 0.408449 | 1.08622× |
| 4 | BF16 | 24 | 0.806006 | 0.780670 | 1.03246× |
| 4 | BF16 | 48 | 1.514886 | 1.513115 | 1.00117× |
| 4 | BF16 | 96 | 2.946226 | 2.947088 | 0.99971× |
| 4 | FP16 | 12 | 0.478149 | 0.412535 | 1.15905× |
| 4 | FP16 | 24 | 0.821719 | 0.782893 | 1.04959× |
| 4 | FP16 | 48 | 1.515075 | 1.519302 | 0.99722× |
| 4 | FP16 | 96 | 2.951808 | 2.951869 | 0.99998× |
| 8 | BF16 | 12 | 0.660781 | 0.615087 | 1.07429× |
| 8 | BF16 | 24 | 1.177820 | 1.130858 | 1.04153× |
| 8 | BF16 | 48 | 2.215143 | 2.176355 | 1.01782× |
| 8 | BF16 | 96 | 4.359669 | 4.314513 | 1.01047× |
| 8 | FP16 | 12 | 0.685422 | 0.625300 | 1.09615× |
| 8 | FP16 | 24 | 1.189269 | 1.137595 | 1.04542× |
| 8 | FP16 | 48 | 2.222356 | 2.174682 | 1.02192× |
| 8 | FP16 | 96 | 4.375149 | 4.316521 | 1.01358× |

The denominator is the complete tuned implementation at
`d45a83981990767fc171e8cd8da5fef5d617a24e`, including SM and both CE
variants. Timing uses CUPTI, cold L2, 5 warmups, 20 samples of 20
collectives per graph, two alternating paired rounds, and the median of
per-sample maximum-rank GPU spans. All 32 span proofs and 192 rank
traces pass enclosure checks for copy-engine and side-stream work. NVML
sampling observes no competing nonzero utilization during the paired
intervals, with maximum query gaps of 1.280/1.261 seconds; this is
sampling-resolution evidence. TP4/TP8 timing processes take
61.053/73.123 physical seconds.

Hardware reports `NVIDIA Graphics Device`, PCI ID `10de:2bb3`, 110 SMs
and 73415 MiB per GPU. Driver 580.95.05; CUDA compiler 13.3.73; PyTorch
2.13.0+cu130.


## 🔍 Related Issues

Builds on merged #4870.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
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

`tests/comm/test_pcie_ipc_compatibility.py` loads the actual JIT module
on non-SM120 hardware and exercises TP4/TP8, BF16/FP16, the original SM
and CE variants, explicit variant-6 fallback, and the normal seed path.
Each route checks changing signed input, exact NCCL agreement, input
preservation, output guards, repeated graph replay, rank delay, and
eager/graph interleaving. These are functional CUDA IPC checks; an
NVLink machine is not used as a PCIe performance denominator.

- Refactored SM120 public tests: **19 passed, 3 expected TP4-island
skips**, 144.864 test / 156 physical seconds.
- Full native protocol regression: **46/46 TP4 and 90/90 TP8** rows,
including independent per-hop references, exact integer checks, both
dtypes, five input distributions, rank delays, and mixed eager/graph
schedules.
- The initial refactor compiles and links shared libraries for **SM80,
SM86, SM89, SM90a, SM100a, SM103a, SM120a and SM121a** in **21.692
physical seconds**. The final host-admission repair repeats this
eight-target compile/link matrix in **21.594 physical seconds**. A check
against the preceding public head reproduces successful SM80 object
compilation followed by a failed shared-library link, which the
unguarded generic leaf fixes.
- Actual **8×H100 / SM90a** module-load and original-path Graph
regression: **5 passed, 0 skipped/failed**, 60.72 pytest / 140.757
managed physical seconds. Both module and group capability keep variant
6 disabled, and all 240 rank/configuration records pass.
- Actual **4×GB200 / SM100, aarch64, CUDA 12.9** module-load and
BF16/FP16 TP4 original-path eager/Graph regression at
`095abe79c476dd2216cd97074c3810624a02960a`: **3 passed, 0
skipped/failed; 2 TP8 cases deselected**. All 64 rank/configuration
records pass, covering the seed, original SM paths, flat CE P1/P2 and
explicit variant-6 fallback with module/group memop disabled. The 11
source inputs match this commit. Module compilation/link/load takes
**27.00 seconds**, pytest reports **24.52 seconds**, bootstrap through
the sealed result takes **100.92 seconds**, the managed step takes
**378.54 seconds**, and task registration to completed result takes
**2408.96 physical seconds**.
- Actual **8×B300 / SM103a, x86_64, CUDA 12.9** module-load and
BF16/FP16 TP4/TP8 original-path eager/Graph regression at
`095abe79c476dd2216cd97074c3810624a02960a`: **5 passed, 0
skipped/failed**. All 24 rank records and 240 rank/configuration rows
pass, covering the seed, original SM paths, flat/island CE and explicit
variant-6 fallback with module/group memop disabled. The 11 source
inputs match this commit. Module compilation/link/load takes **33.44
seconds**, pytest reports **92.61 seconds**, bootstrap through the
sealed result takes **227.33 seconds**, the managed step takes **364.58
seconds**, and allocation request to completed result takes **6285.56
physical seconds**.
- Actual **8×B200 / SM100a, x86_64, CUDA 12.9** module-load and
BF16/FP16 TP8 original-path eager/Graph regression at
`095abe79c476dd2216cd97074c3810624a02960a`: **3 passed, 0
skipped/failed; 2 TP4 cases deselected**. All 16 rank records and 176
rank/configuration rows pass, including the seed, original SM paths, TP8
flat-staged path, flat/island CE P1/P2 and explicit variant-6 fallback
with memop disabled. Module compilation/link/load takes **36.03
seconds**, pytest reports **44.89 seconds**, bootstrap through the
sealed result takes **186.19 seconds**, and submission to the completed
managed result takes **248.17 physical seconds**. This B200 run covers
TP8; the separate GB200 run above supplies SM100 TP4 coverage.
Result/coverage summaries and source hashes were retained; raw per-rank
logs and the test library were removed during allocation cleanup.
- Hardware coverage limits: **SM80, SM86, SM89 and SM121 have
compile/link evidence only**. A100/SM80 hardware qualification is
omitted from this validation scope.
- `pre-commit run --all-files`: all applicable hooks pass. Refactor
formatting preserves all C++ lexical tokens; generated leaf source
tokens also match its regeneration.
- Compute Sanitizer **synccheck 4/4** reports zero errors; **racecheck
4/4** reports zero hazards/errors/warnings for TP4/TP8 and both dtypes
through actual-library graph replay with changing input. Every command
is independently bounded by `timeout --signal=KILL 20s`; observed
durations are 1.52–3.92 seconds.
- Fresh NCU on the reused native 6 MiB BF16 add: **13.792 us, 912.724
GB/s, 71.506% DRAM throughput, 34 registers/thread, 64 CTAs**.
Global-memory dependencies and long-scoreboard stalls remain its
bottleneck. These diagnostics are separate from collective timing.
- `nvdisasm` of the actual linked module confirms the original packed
add/monotonic handshake kernels and the single generated system-acquire
polling/clear leaf.

The bounded SM120 protocol/timing/sanitizer controller takes 208.073
physical seconds. Source and actual library identities are bound to the
refactor commit; earlier generated-add measurements are not reused for
this table. The repository-wide GPU test suite was not run. Public
non-GPU CI passes review, documentation build, public API/documentation
checks, pre-commit and labeling. An earlier GPU CI attempt was blocked
by repository authorization. The subsequent authorized three-file run is
reported below.

The subsequent host-admission repair is in
`095abe79c476dd2216cd97074c3810624a02960a`: `cuStreamWriteValue32` links
the CUDA v2 symbol, so the deprecated v1 opt-in attribute must not
disable its default-supported 32-bit writes. On four real SM120 devices
the actual rebuilt module admits the path; TP4 BF16/FP16 Graph
regression passes **2/2 without skips** (24.240 physical seconds
including the positive module probe). All eight targets compile and link
again in **21.594 seconds**, and pre-commit passes. Both embedded SM120
cubins are byte-identical to the qualified refactor library, so the
timing and sanitizer results above remain measurements of the same
device implementation. The H100 run above binds to the preceding
refactor commit `231dbc28ea2f52ea8a08c3d83a7b15364bc15964`; the GB200,
B200 and B300 runs above use the repaired admission source.


Physical turnaround recorded for final delivery is **14,046 seconds (3h
54m 06s)**, from **2026-09-12 21:33:06 UTC** through **2026-09-13
01:27:12 UTC**. This includes scheduling waits, failed infrastructure
startup attempts, source refinement, validation, final CI and
publication review; the GPU-only comparative timings are reported
separately above.

<!-- pcie-cross-architecture-performance -->

## Performance on H100, GB200, GB300, B200 and B300

These are fresh measurements of the actual native modules on each named
GPU family. The 64-row matrix covers BF16/FP16 and per-rank input
payloads of 12/24/48/96 MiB; H100/B200/B300 cover TP4 and TP8, and
GB200/GB300 cover TP4.

Baseline: `d45a83981990767fc171e8cd8da5fef5d617a24e`, the complete
original SM+CE implementation whose seven relevant source files match
merged #4870. Candidate: `095abe79c476dd2216cd97074c3810624a02960a`. The
optimized stream-publication protocol stays disabled on these non-SM120
GPUs.

The complete original production tuner selects a configuration on each
measured platform/TP/dtype/shape, then that configuration is frozen and
applied unchanged to both revisions. The production candidate grid and
survivor screen are retained. This is a comparison at the same selected
configuration; candidate timings are held out from tuning and are not
independently retuned winners.

Reportable timing uses strict CUPTI activity tracing, five warmups and
20 samples of 20 collectives per CUDA Graph. L2 is flushed before each
sampled graph, not between its 20 collectives. Two paired rounds run A/B
then B/A. For each sample, take the maximum GPU span across ranks and
divide by 20; take the median of those samples, then the median across
paired rounds. Boundary-marker trace proofs cover the collective,
including copy-engine and side-stream work. Changed-input Graph/eager
checks and post-timing correctness pass on the measured configurations.

The container PyTorch build lacks the retained-source-graph API. For
diagnostic DAG inspection only, CUDA driver capture/instantiate/replay
retains the source graph using preallocated native launches inside the
PyTorch graph stream context. Reported timing and the independent
ordinary-graph span proof continue to use ordinary
`torch.cuda.CUDAGraph()` graphs.

Speedup is baseline/candidate; a value below 1 means the candidate was
slower in this measurement. The tables retain round medians and observed
sample spread rather than applying an invented pass/fail performance
threshold. For SM variants, `b` is block count and `t` is thread count.
For CE variants, `hint` is the requested depth and `effective` is the
depth observed in the captured trace.

### H100

H100 timing uses native CUPTI 12.9 (API 27), cupti-python 12.8.0 and
cuda-bindings 12.8.0 with the CUDA 12.9 forward-compatibility driver
575.51.03. Native activity and Graph callbacks retain runtime, driver,
kernel and copy records in the existing timing and trace analysis. These
are the actual measurement dependencies; initial module-build profiling
metadata describes the earlier environment.

Observed device: **NVIDIA H100 80GB HBM3**, SM90; CPU `x86_64`; TP 4, 8.
CUDA runtime 12.9, driver 535.216.03, PyTorch
`2.8.0a0+5228986c39.nv25.5`.

Saved node topology reports NVLink NV18. Automatic cache profile:
`rootcplx-noswitch`. This profile records PCIe ancestry; it does not
imply that the measured transfers bypass NVLink.

| Rows | Baseline mean ms | Candidate mean ms | Ratio of means |
Geometric mean speedup | Worst shape speedup |
|---:|---:|---:|---:|---:|---:|
| 16 | 0.267771 | 0.268482 | 0.997351× | 0.997754× | 0.982047× |

Worst observed row: TP4 BF16 48 MiB, 0.260970 → 0.265741 ms. Across
individual paired measurements, the relative sample standard deviation
has median 1.047% and maximum 17.560% (population standard deviation
divided by mean over the 20 maximum-rank samples).

| TP | Type | MiB | Frozen launch configuration | Baseline ms |
Candidate ms | Speedup | Baseline r0 / r1 ms | Candidate r0 / r1 ms |
|---:|---|---:|---|---:|---:|---:|---:|---:|
| 4 | BF16 | 12 | SM staged ring: b=64, t=256 | 0.105602 | 0.105652 |
0.999532× | 0.105579 / 0.105626 | 0.105685 / 0.105619 |
| 4 | BF16 | 24 | SM staged ring: b=128, t=1024 | 0.141261 | 0.141601 |
0.997603× | 0.140635 / 0.141887 | 0.141956 / 0.141246 |
| 4 | BF16 | 48 | SM staged ring: b=128, t=1024 | 0.260970 | 0.265741 |
0.982047× | 0.259939 / 0.262000 | 0.268238 / 0.263243 |
| 4 | BF16 | 96 | SM staged ring: b=128, t=1024 | 0.534652 | 0.535674 |
0.998092× | 0.535813 / 0.533491 | 0.534265 / 0.537083 |
| 4 | FP16 | 12 | SM staged ring: b=128, t=512 | 0.085809 | 0.085576 |
1.002730× | 0.085763 / 0.085856 | 0.085522 / 0.085629 |
| 4 | FP16 | 24 | SM staged ring: b=64, t=1024 | 0.146540 | 0.147962 |
0.990387× | 0.145627 / 0.147452 | 0.146988 / 0.148936 |
| 4 | FP16 | 48 | SM staged ring: b=128, t=1024 | 0.261707 | 0.261669 |
1.000146× | 0.262071 / 0.261343 | 0.261477 / 0.261860 |
| 4 | FP16 | 96 | SM staged ring: b=128, t=1024 | 0.528898 | 0.532892 |
0.992504× | 0.530526 / 0.527269 | 0.532690 / 0.533094 |
| 8 | BF16 | 12 | SM staged: b=128, t=512 | 0.090480 | 0.090484 |
0.999957× | 0.090489 / 0.090471 | 0.090458 / 0.090510 |
| 8 | BF16 | 24 | SM staged ring: b=128, t=1024 | 0.170841 | 0.170692 |
1.000872× | 0.171367 / 0.170315 | 0.170438 / 0.170947 |
| 8 | BF16 | 48 | SM staged: b=128, t=1024 | 0.288719 | 0.288896 |
0.999386× | 0.288761 / 0.288677 | 0.288888 / 0.288905 |
| 8 | BF16 | 96 | SM staged: b=96, t=1024 | 0.575889 | 0.576709 |
0.998578× | 0.577420 / 0.574358 | 0.578945 / 0.574474 |
| 8 | FP16 | 12 | SM staged: b=96, t=1024 | 0.091508 | 0.091411 |
1.001068× | 0.091566 / 0.091451 | 0.091340 / 0.091481 |
| 8 | FP16 | 24 | SM staged: b=128, t=1024 | 0.155759 | 0.155724 |
1.000225× | 0.155737 / 0.155781 | 0.155685 / 0.155763 |
| 8 | FP16 | 48 | SM staged: b=128, t=1024 | 0.288749 | 0.288786 |
0.999872× | 0.288886 / 0.288611 | 0.288774 / 0.288798 |
| 8 | FP16 | 96 | SM staged: b=128, t=1024 | 0.556951 | 0.556247 |
1.001265× | 0.555428 / 0.558474 | 0.555304 / 0.557191 |

Successful-attempt elapsed time: environment/source/module setup
**435.409 s**; correctness/trace checks and paired measurement
controller **407.566 s** (including tuning only where it ran in that
attempt). These successful-attempt work-unit times exclude earlier
failed attempts and scheduling waits; they are separate from both
end-to-end turnaround and the GPU milliseconds above.

Original tuner preparation completed separately in **248.713 s** and its
four sealed TP/dtype results were reused. The successful measurement
controller above excludes that preparation. Its managed execution step
took **415.283 s**, including step startup/teardown.

### GB200

Observed device: **NVIDIA GB200**, SM100; CPU `aarch64`; TP 4. CUDA
runtime 12.9, driver 580.126.20, PyTorch `2.8.0a0+5228986c39.nv25.5`.

Saved node topology reports NVLink NV18. Automatic cache profile:
`rootcplx-noswitch`. This profile records PCIe ancestry; it does not
imply that the measured transfers bypass NVLink.

| Rows | Baseline mean ms | Candidate mean ms | Ratio of means |
Geometric mean speedup | Worst shape speedup |
|---:|---:|---:|---:|---:|---:|
| 8 | 0.143053 | 0.143131 | 0.999452× | 0.996491× | 0.983366× |

Worst observed row: TP4 FP16 12 MiB, 0.036536 → 0.037154 ms. Across
individual paired measurements, the relative sample standard deviation
has median 4.363% and maximum 29.553% (population standard deviation
divided by mean over the 20 maximum-rank samples).

| TP | Type | MiB | Frozen launch configuration | Baseline ms |
Candidate ms | Speedup | Baseline r0 / r1 ms | Candidate r0 / r1 ms |
|---:|---|---:|---|---:|---:|---:|---:|---:|
| 4 | BF16 | 12 | SM staged: b=96, t=1024 | 0.036399 | 0.036531 |
0.996386× | 0.036437 / 0.036361 | 0.036434 / 0.036627 |
| 4 | BF16 | 24 | SM staged: b=64, t=1024 | 0.073799 | 0.074640 |
0.988735× | 0.073797 / 0.073802 | 0.075339 / 0.073941 |
| 4 | BF16 | 48 | SM staged: b=96, t=1024 | 0.159321 | 0.159462 |
0.999115× | 0.163911 / 0.154731 | 0.154879 / 0.164045 |
| 4 | BF16 | 96 | SM staged ring: b=128, t=1024 | 0.299863 | 0.299873 |
0.999968× | 0.299689 / 0.300037 | 0.300180 / 0.299566 |
| 4 | FP16 | 12 | SM staged: b=96, t=1024 | 0.036536 | 0.037154 |
0.983366× | 0.036552 / 0.036519 | 0.037830 / 0.036478 |
| 4 | FP16 | 24 | SM staged: b=64, t=1024 | 0.073876 | 0.073804 |
1.000986× | 0.073893 / 0.073860 | 0.073769 / 0.073838 |
| 4 | FP16 | 48 | SM staged: b=96, t=1024 | 0.163912 | 0.163888 |
1.000146× | 0.163943 / 0.163881 | 0.163915 / 0.163861 |
| 4 | FP16 | 96 | SM staged ring: b=128, t=1024 | 0.300717 | 0.299700 |
1.003395× | 0.301548 / 0.299887 | 0.299793 / 0.299606 |

TP8 was not run: the measured Grace node exposes four GPUs, while this
CUDA IPC API is intra-node only.

Successful-attempt elapsed time: environment/source/module setup
**39.995 s**; correctness/trace checks and paired measurement controller
**159.709 s** (including tuning only where it ran in that attempt).
These successful-attempt work-unit times exclude earlier failed attempts
and scheduling waits; they are separate from both end-to-end turnaround
and the GPU milliseconds above.

### GB300

Observed device: **NVIDIA GB300**, SM103; CPU `aarch64`; TP 4. CUDA
runtime 12.9, driver 580.167.08, PyTorch `2.8.0a0+5228986c39.nv25.5`.

Saved node topology reports NVLink NV18. Automatic cache profile:
`rootcplx-noswitch`. This profile records PCIe ancestry; it does not
imply that the measured transfers bypass NVLink.

| Rows | Baseline mean ms | Candidate mean ms | Ratio of means |
Geometric mean speedup | Worst shape speedup |
|---:|---:|---:|---:|---:|---:|
| 8 | 0.145567 | 0.145749 | 0.998749× | 0.999715× | 0.974835× |

Worst observed row: TP4 BF16 48 MiB, 0.164297 → 0.168539 ms. Across
individual paired measurements, the relative sample standard deviation
has median 0.588% and maximum 55.370% (population standard deviation
divided by mean over the 20 maximum-rank samples).

| TP | Type | MiB | Frozen launch configuration | Baseline ms |
Candidate ms | Speedup | Baseline r0 / r1 ms | Candidate r0 / r1 ms |
|---:|---|---:|---|---:|---:|---:|---:|---:|
| 4 | BF16 | 12 | SM staged: b=128, t=256 | 0.042893 | 0.042946 |
0.998760× | 0.042899 / 0.042887 | 0.042687 / 0.043206 |
| 4 | BF16 | 24 | SM staged: b=96, t=512 | 0.076914 | 0.076874 |
1.000525× | 0.076185 / 0.077644 | 0.076179 / 0.077570 |
| 4 | BF16 | 48 | SM staged: b=64, t=1024 | 0.164297 | 0.168539 |
0.974835× | 0.168441 / 0.160154 | 0.168509 / 0.168568 |
| 4 | BF16 | 96 | SM staged ring: b=96, t=1024 | 0.304389 | 0.303710 |
1.002237× | 0.304182 / 0.304597 | 0.303901 / 0.303519 |
| 4 | FP16 | 12 | SM staged: b=128, t=512 | 0.039521 | 0.039584 |
0.998403× | 0.040169 / 0.038873 | 0.038937 / 0.040231 |
| 4 | FP16 | 24 | SM staged: b=96, t=1024 | 0.069949 | 0.068692 |
1.018302× | 0.069945 / 0.069953 | 0.068582 / 0.068801 |
| 4 | FP16 | 48 | SM staged ring: b=96, t=1024 | 0.168332 | 0.167541 |
1.004719× | 0.167803 / 0.168860 | 0.167554 / 0.167528 |
| 4 | FP16 | 96 | SM staged ring: b=128, t=1024 | 0.298237 | 0.298105 |
1.000442× | 0.298462 / 0.298011 | 0.298103 / 0.298107 |

TP8 was not run: the measured Grace node exposes four GPUs, while this
CUDA IPC API is intra-node only.

Successful-attempt elapsed time: environment/source/module setup
**40.142 s**; correctness/trace checks and paired measurement controller
**179.829 s** (including tuning only where it ran in that attempt).
These successful-attempt work-unit times exclude earlier failed attempts
and scheduling waits; they are separate from both end-to-end turnaround
and the GPU milliseconds above.

### B200

Observed device: **NVIDIA B200**, SM100; CPU `x86_64`; TP 4, 8. CUDA
runtime 12.9, driver 610.57.04, PyTorch `2.8.0a0+5228986c39.nv25.5`.

Saved node topology reports NVLink NV18. Automatic cache profile:
`rootcplx-noswitch`. This profile records PCIe ancestry; it does not
imply that the measured transfers bypass NVLink.

| Rows | Baseline mean ms | Candidate mean ms | Ratio of means |
Geometric mean speedup | Worst shape speedup |
|---:|---:|---:|---:|---:|---:|
| 16 | 0.171413 | 0.170973 | 1.002574× | 1.002954× | 0.996807× |

Worst observed row: TP4 FP16 48 MiB, 0.166197 → 0.166729 ms. Across
individual paired measurements, the relative sample standard deviation
has median 1.220% and maximum 50.158% (population standard deviation
divided by mean over the 20 maximum-rank samples).

| TP | Type | MiB | Frozen launch configuration | Baseline ms |
Candidate ms | Speedup | Baseline r0 / r1 ms | Candidate r0 / r1 ms |
|---:|---|---:|---|---:|---:|---:|---:|---:|
| 4 | BF16 | 12 | SM staged: b=128, t=512 | 0.038854 | 0.038740 |
1.002936× | 0.038847 / 0.038861 | 0.038756 / 0.038724 |
| 4 | BF16 | 24 | SM staged: b=96, t=256 | 0.098490 | 0.096013 |
1.025789× | 0.096915 / 0.100064 | 0.095872 / 0.096155 |
| 4 | BF16 | 48 | SM staged: b=96, t=1024 | 0.159342 | 0.159363 |
0.999868× | 0.164158 / 0.154525 | 0.164122 / 0.154604 |
| 4 | BF16 | 96 | SM staged: b=128, t=1024 | 0.353927 | 0.354638 |
0.997997× | 0.353942 / 0.353913 | 0.354631 / 0.354645 |
| 4 | FP16 | 12 | SM staged: b=64, t=1024 | 0.039060 | 0.039137 |
0.998050× | 0.039042 / 0.039078 | 0.039121 / 0.039153 |
| 4 | FP16 | 24 | SM staged: b=64, t=1024 | 0.078636 | 0.078808 |
0.997809× | 0.078547 / 0.078725 | 0.078778 / 0.078839 |
| 4 | FP16 | 48 | SM staged: b=128, t=1024 | 0.166197 | 0.166729 |
0.996807× | 0.166655 / 0.165739 | 0.166739 / 0.166719 |
| 4 | FP16 | 96 | SM staged: b=96, t=1024 | 0.359027 | 0.359038 |
0.999969× | 0.359108 / 0.358946 | 0.359004 / 0.359073 |
| 8 | BF16 | 12 | SM staged: b=128, t=1024 | 0.081154 | 0.081163 |
0.999886× | 0.081174 / 0.081135 | 0.081195 / 0.081132 |
| 8 | BF16 | 24 | SM flat staged: b=64, t=512 | 0.099559 | 0.099547 |
1.000122× | 0.099645 / 0.099473 | 0.099562 / 0.099531 |
| 8 | BF16 | 48 | SM flat staged: b=96, t=1024 | 0.197346 | 0.191610 |
1.029938× | 0.192143 / 0.202549 | 0.191084 / 0.192136 |
| 8 | BF16 | 96 | SM staged: b=128, t=1024 | 0.348906 | 0.348998 |
0.999738× | 0.348888 / 0.348924 | 0.349095 / 0.348900 |
| 8 | FP16 | 12 | SM flat staged: b=64, t=512 | 0.049854 | 0.049949 |
0.998095× | 0.049781 / 0.049926 | 0.049917 / 0.049981 |
| 8 | FP16 | 24 | SM flat staged: b=96, t=512 | 0.091328 | 0.091428 |
0.998902× | 0.091351 / 0.091304 | 0.091433 / 0.091423 |
| 8 | FP16 | 48 | SM staged: b=96, t=1024 | 0.203558 | 0.203254 |
1.001497× | 0.203600 / 0.203517 | 0.202786 / 0.203722 |
| 8 | FP16 | 96 | SM staged ring: b=128, t=1024 | 0.377373 | 0.377155 |
1.000578× | 0.377198 / 0.377549 | 0.376756 / 0.377554 |

Successful-attempt elapsed time: environment/source/module setup
**509.063 s**; correctness/trace checks and paired measurement
controller **602.038 s** (including tuning only where it ran in that
attempt). These successful-attempt work-unit times exclude earlier
failed attempts and scheduling waits; they are separate from both
end-to-end turnaround and the GPU milliseconds above.

B200 setup, measurement and read-only collection logs emitted
`driverInitFileInfo/init result=11` after their successful result
records. All 64 B200 build/round measurements and their
trace/correctness checks passed; the diagnostic's origin was not
established.

### B300

Observed device: **NVIDIA B300 SXM6 AC**, SM103; CPU `x86_64`; TP 4, 8.
CUDA runtime 12.9, driver 580.126.09, PyTorch
`2.8.0a0+5228986c39.nv25.5`.

Saved node topology reports NVLink NV18. Automatic cache profile:
`rootcplx-noswitch`. This profile records PCIe ancestry; it does not
imply that the measured transfers bypass NVLink.

| Rows | Baseline mean ms | Candidate mean ms | Ratio of means |
Geometric mean speedup | Worst shape speedup |
|---:|---:|---:|---:|---:|---:|
| 16 | 0.163397 | 0.162827 | 1.003499× | 1.002599× | 0.949393× |

Worst observed row: TP4 BF16 48 MiB, 0.154531 → 0.162769 ms. Across
individual paired measurements, the relative sample standard deviation
has median 1.990% and maximum 14.547% (population standard deviation
divided by mean over the 20 maximum-rank samples).

| TP | Type | MiB | Frozen launch configuration | Baseline ms |
Candidate ms | Speedup | Baseline r0 / r1 ms | Candidate r0 / r1 ms |
|---:|---|---:|---|---:|---:|---:|---:|---:|
| 4 | BF16 | 12 | SM staged: b=96, t=512 | 0.038462 | 0.038448 |
1.000374× | 0.038442 / 0.038482 | 0.038383 / 0.038512 |
| 4 | BF16 | 24 | SM staged: b=96, t=1024 | 0.067810 | 0.067842 |
0.999522× | 0.067823 / 0.067797 | 0.067804 / 0.067881 |
| 4 | BF16 | 48 | SM staged: b=96, t=1024 | 0.154531 | 0.162769 |
0.949393× | 0.146163 / 0.162900 | 0.162739 / 0.162798 |
| 4 | BF16 | 96 | SM staged ring: b=96, t=1024 | 0.312140 | 0.311623 |
1.001659× | 0.312400 / 0.311881 | 0.311729 / 0.311517 |
| 4 | FP16 | 12 | SM staged: b=128, t=512 | 0.037403 | 0.037258 |
1.003876× | 0.037405 / 0.037400 | 0.037315 / 0.037202 |
| 4 | FP16 | 24 | SM staged: b=96, t=1024 | 0.067836 | 0.067848 |
0.999822× | 0.067853 / 0.067819 | 0.067881 / 0.067815 |
| 4 | FP16 | 48 | SM staged: b=128, t=1024 | 0.167887 | 0.165579 |
1.013939× | 0.167912 / 0.167861 | 0.168004 / 0.163153 |
| 4 | FP16 | 96 | SM staged ring: b=96, t=1024 | 0.311538 | 0.312791 |
0.995994× | 0.311516 / 0.311560 | 0.311420 / 0.314162 |
| 8 | BF16 | 12 | SM flat staged: b=128, t=256 | 0.048783 | 0.048770 |
1.000270× | 0.048766 / 0.048800 | 0.048763 / 0.048777 |
| 8 | BF16 | 24 | SM flat staged: b=128, t=512 | 0.088482 | 0.088376 |
1.001194× | 0.088522 / 0.088442 | 0.088393 / 0.088360 |
| 8 | BF16 | 48 | SM flat staged: b=64, t=1024 | 0.209115 | 0.199421 |
1.048610× | 0.213518 / 0.204712 | 0.197144 / 0.201699 |
| 8 | BF16 | 96 | SM staged ring: b=128, t=512 | 0.420211 | 0.420325 |
0.999729× | 0.420199 / 0.420223 | 0.420372 / 0.420278 |
| 8 | FP16 | 12 | SM flat staged: b=128, t=256 | 0.048821 | 0.048830 |
0.999811× | 0.048833 / 0.048809 | 0.048826 / 0.048835 |
| 8 | FP16 | 24 | SM flat staged: b=128, t=512 | 0.088413 | 0.088468 |
0.999380× | 0.088422 / 0.088403 | 0.088462 / 0.088473 |
| 8 | FP16 | 48 | SM flat staged: b=96, t=1024 | 0.201680 | 0.195567 |
1.031257× | 0.201816 / 0.201544 | 0.201857 / 0.189278 |
| 8 | FP16 | 96 | SM staged: b=128, t=1024 | 0.351238 | 0.351319 |
0.999769× | 0.351060 / 0.351416 | 0.351397 / 0.351242 |

Successful-attempt elapsed time: environment/source/module setup
**522.074 s**; correctness/trace checks and paired measurement
controller **718.872 s** (including tuning only where it ran in that
attempt). These successful-attempt work-unit times exclude earlier
failed attempts and scheduling waits; they are separate from both
end-to-end turnaround and the GPU milliseconds above.

These figures characterize the observed hardware and interconnects,
including NVLink where present; they are not PCIe-link bandwidth
measurements. No cross-family average latency is reported. The receipts
do not establish pinned clocks or continuous absence of external
interference. The two-round spread is descriptive evidence, not a
statistical confidence interval. The existing SM120 measurements remain
a separate historical qualification and were not rerun here.

End-to-end physical turnaround through verified report delivery is
**18787.932 seconds** (5.219 hours), from **2026-09-13 01:39:28 UTC**
through **2026-09-13 06:52:35 UTC**. This includes scheduling, setup,
measurements, validation, publication and readback. The closing
timestamp-only update follows this checkpoint.


B300's worst observed row, TP4 BF16 48 MiB, has 5.330% greater candidate
latency. Baseline round medians are 0.146163/0.162900 ms and candidate
medians are 0.162739/0.162798 ms; this variation is retained without
assigning a cause.

The diagnostic source graph uses preallocated CUDA driver capture
because this development PyTorch build lacks the retained-graph API.
Timing uses ordinary PyTorch graphs. Graph edge metadata is copied into
owned buffers to avoid a CUDA Python 13.0.3 lifetime bug. Actual
adapter, binding and native module identities are retained with the
measurement records.

### Requested three-file CI

[One
comment](https://github.com/flashinfer-ai/flashinfer/pull/5169#issuecomment-5649984234)
requested all three files together:

```text
@flashinfer-bot run tests/comm/test_pcie_ipc_ce_ring.py tests/comm/test_pcie_ipc_compatibility.py tests/comm/test_pcie_ipc_tuning.py
```

[Run 34730937773, attempt
2](https://github.com/flashinfer-ai/flashinfer/actions/runs/34730937773),
on `095abe79c476dd2216cd97074c3810624a02960a`, completed with
**success**. All three targeted GPU jobs completed successfully:

| Targeted job | Passed | Failed | Runner skipped category |
|---|---:|---:|---:|
|
[H100](https://github.com/flashinfer-ai/flashinfer/actions/runs/34730937773/job/103655834703)
| 33 | 0 | 33 |
|
[A10G](https://github.com/flashinfer-ai/flashinfer/actions/runs/34730937773/job/103655834573)
| 33 | 0 | 33 |
|
[T4](https://github.com/flashinfer-ai/flashinfer/actions/runs/34730937773/job/103655834672)
| 32 | 0 | 34 |

These counts include substantial skipped coverage.
`test_pcie_ipc_ce_ring.py` has 28 skipped cases on each job.
`test_pcie_ipc_compatibility.py` has one module-load pass and four skips
on H100/A10G, and five skips on T4. `test_pcie_ipc_tuning.py` has 32
passes and one skipped-category case on each job; H100 JUnit identifies
the latter as the existing strict xfail for a seed requesting three ring
blocks while `TUNE_BLOCKS` omits three. A10G/T4 batch logs preserve the
aggregate counts but do not provide uploaded JUnit classification.

H100 JUnit records insufficient visible GPUs for TP4/TP8; the CI runner
assigns one GPU per test worker. The same one-GPU placement and
unchanged source guards explain the A10G counts; T4 additionally falls
below the module test's SM80/BF16 minimum. Thus these targeted job
successes do **not** establish TP4/TP8 collective correctness or Graph
coverage.

All four AOT build/import jobs (x64 and arm64, CUDA 12.9 and 13.0)
completed successfully. Attempt 1 failed during Docker image extraction
when the daemon/socket became unavailable, before the AOT workload
started; sibling matrix jobs were cancelled. That attempt supplies no
kernel-test failure evidence. Attempt 2 retried the same run without
another trigger comment.
<!-- end pcie-cross-architecture-performance -->

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added an optimized PCIe IPC all-reduce mode for supported SM120
hardware.
- Added automatic detection and configuration of memory-operation
support.
- Added tuning support for the new mode on supported 4- and 8-GPU
configurations.

- **Bug Fixes**
  - Improved workspace reuse across mixed communication modes.
- Added fallback behavior when memory-operation support is unavailable.
  - Preserved PCIe IPC operation on supported non-SM120 hardware.

- **Tests**
- Expanded coverage for capability detection, tuning, graph replay,
compatibility, and mixed-mode workspace reuse.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: root <root@R6KD-CX8aaS-GPU-10.cm.cluster>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [93e9eef](https://github.com/flashinfer-ai/flashinfer/commit/93e9eef092c11bc93a6f432a16404054e85d19c5)

- **作者**: Shanli Xing
- **时间**: 2026-09-13T09:14:40Z
- **提交信息**: feat(cake_alpha_moe): add optimized Blackwell W8A8 expert up/down compute (#4287)

Add the Blackwell W8A8 expert up/down operator, optimize output scheduling and scale reuse, and align the reference scale rounding.

Performance and validation evidence: https://github.com/flashinfer-ai/flashinfer/pull/4287

Co-authored-by: Shanli Xing <me@xsl.sh>
Co-authored-by: Yingyi Huang <52445717+yyihuang@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4388
- **最后更新**: 2026-09-13T23:04:43Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34505
- **最后更新**: 2026-09-13T18:17:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
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


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13092
- **最后更新**: 2026-09-13T15:08:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35909
- **最后更新**: 2026-09-13T23:55:41Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 11
- **主要提交者**: Jimmy Shong, ishandhanani, lz

## AI分析总结

# SGLang 昨日提交分析总结

## 1. 主要更新类型

本批次 14 个提交以**功能新增**和**Bug修复**为主，辅以**重构**、**版本升级**和**测试补充**：

- **功能新增**：PD 路由支持 `/v1/responses`、Unified Cache 外部链接器支持 MTP/EAGLE/DSpark 草稿 KV 缓存、Qwen3.8 在 DGX Spark 上启用 NVFP4。
- **Bug修复**：HiCache 缓冲预取锁释放、diffusion 序列 gather 连续性、不可读 checkpoint 回退、router bucket 上下文限制简化。
- **重构**：统一缓存组件去除冗余 `_component` 后缀。
- **版本升级**：sgl-kernel 升至 0.4.7、FlashMLA 升级至 v4.1 内核。
- **测试/治理**：新增 muse_glimmer_format 单测、补充 HiSparse 代码负责人。

## 2. 关键变更点与项目方向

- **PD 分离架构持续深化**：`/v1/responses` 接入 HTTP PD 路由器，同时将持久化默认关闭（`--enable-response-store` 门控），体现对 PD 场景 API 覆盖与安全默认值的双重关注。
- **统一缓存（Unified Cache）演进**：外部链接器支持草稿模型 KV 缓存，配合组件命名重构，说明项目正系统性地整合多级缓存体系。
- **HiCache 稳定性增强**：锁释放与 host store 事件发布，强化存储预取场景下的资源管理与可观测性。
- **新硬件/新模型适配**：DGX Spark 上的 NVFP4 与 Qwen3.8 支持，延续项目对前沿硬件与模型生态的快速跟进。

## 3. 对项目的影响与潜在意义

- PD 路由对 `/v1/responses` 的支持，使 SGLang 在 OpenAI 兼容 API 上更完整，有利于生产环境统一接入。
- 草稿 KV 缓存纳入统一链接器，为投机解码（MTP/EAGLE）在缓存复用层面铺路，可能显著提升推理吞吐。
- 默认关闭响应持久化，降低误用风险，体现对生产安全的审慎态度。
- 多个 diffusion 修复表明多模态/扩散推理路径正被积极打磨。

## 4. 值得关注的技术点

- FlashMLA 采用 fork rebase head 的 v4.1 内核，暗示上游与定制分支的协同策略。
- HiCache 的锁释放与事件发布机制，是存储预取并发正确性的关键。
- 组件命名去后缀重构虽小，但反映代码库向统一抽象收敛的意图。
- 多处提交由 Claude 协同署名，显示 AI 辅助开发在项目中的实际参与。

## 5. 结合 README 的项目发展影响

SGLang 定位为高性能 LLM 服务引擎，强调快速部署与广泛模型支持。本批提交从三个维度推进这一目标：**API 完整性**（PD 路由扩展）、**推理效率**（缓存与投机解码整合）、**硬件前沿性**（NVFP4/DGX Spark）。同时，稳定性修复与默认安全门控表明项目正从功能扩张转向生产可用性打磨，符合其作为 PyPI 高下载量推理框架的成熟化路径。

## 详细提交记录

### [4358a16](https://github.com/sgl-project/sglang/commit/4358a1617cad734fc37bf53d9e5c2092bd43d075)

- **作者**: sglang-bot
- **时间**: 2026-09-13T22:48:50Z
- **提交信息**: chore: bump sgl-kernel version to 0.4.7 (#39324)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [5ebb160](https://github.com/sgl-project/sglang/commit/5ebb16005d2804bc3f87c689e3333a3734d80bf7)

- **作者**: Baizhou Zhang
- **时间**: 2026-09-13T22:43:19Z
- **提交信息**: [DeepSeek-V4.1] Bump FlashMLA to the fork's rebase head (v4.1 kernels) (#39171)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>

### [ff228d1](https://github.com/sgl-project/sglang/commit/ff228d11fe0b517c4c5a8b679212de9e82d0a6fa)

- **作者**: Shuwen Wang
- **时间**: 2026-09-13T20:47:21Z
- **提交信息**: [HiCache] Release buffer prefetch anchor locks during storage cleanup (#38483)

### [ddc1df1](https://github.com/sgl-project/sglang/commit/ddc1df1203036c97ef2398ef4e2d012301c4c17f)

- **作者**: ishandhanani
- **时间**: 2026-09-13T19:27:59Z
- **提交信息**: fix(router): simplify bucket context limit check (#39259)

Signed-off-by: Ishan Dhanani <ishandhanani@gmail.com>

### [6220f45](https://github.com/sgl-project/sglang/commit/6220f45d8e9a932857b5490e81d1fe9bfc70e841)

- **作者**: lz
- **时间**: 2026-09-13T14:48:13Z
- **提交信息**: [PD] Add /v1/responses support to the HTTP PD router (#36141)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [7f1f8c7](https://github.com/sgl-project/sglang/commit/7f1f8c706ac000b7a84ea0bda05135fc4177c6ca)

- **作者**: Shuwen Wang
- **时间**: 2026-09-13T13:38:20Z
- **提交信息**: [mem_cache][10/N] refactor: drop the redundant _component suffix in unified_cache/components (#35644)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [14a131a](https://github.com/sgl-project/sglang/commit/14a131ad5b43bbb9dd7c5e91968e21e0c6432e4c)

- **作者**: Shangming Cai
- **时间**: 2026-09-13T13:20:47Z
- **提交信息**: [PD][OpenAI] Gate /v1/responses persistence behind --enable-response-store, default off (#39122)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [f9fca05](https://github.com/sgl-project/sglang/commit/f9fca0580340a0c3ff4d5a3fc78f03a7a60de3ca)

- **作者**: Mick
- **时间**: 2026-09-13T12:30:52Z
- **提交信息**: [diffusion] fix: make the sp sequence gather pass contiguous shards (#39291)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [9ffe548](https://github.com/sgl-project/sglang/commit/9ffe548738d8a4ef52d76eec269f9e5ce3ab5a54)

- **作者**: Mick
- **时间**: 2026-09-13T12:30:24Z
- **提交信息**: [diffusion] fix: don't route an unreadable checkpoint into the native fallback (#39292)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [14b647c](https://github.com/sgl-project/sglang/commit/14b647cf27d7f2c1a3764841f7d3770ff9f9e7d6)

- **作者**: Shuwen Wang
- **时间**: 2026-09-13T10:42:33Z
- **提交信息**: chore: add HiSparse coordinator and allocator code owners (#38682)

### [d24eaca](https://github.com/sgl-project/sglang/commit/d24eacaecd56090f16134f75d0ba72cc37915544)

- **作者**: Hritik Raj
- **时间**: 2026-09-13T10:40:02Z
- **提交信息**: [Test] Add unit test for muse_glimmer_format (#37015)

Signed-off-by: Hritik003 <hritik.raj@nutanix.com>

### [7078e5f](https://github.com/sgl-project/sglang/commit/7078e5ffbc71f9f31d07018aff2f32530dac781a)

- **作者**: Jundong Liu
- **时间**: 2026-09-13T10:29:14Z
- **提交信息**: [HiCache] Publish a host store event for storage-prefetch refills (#38486)

Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [a7cf4a6](https://github.com/sgl-project/sglang/commit/a7cf4a6fbcde851cc35bc667966415abeb7362c1)

- **作者**: huangtingwei
- **时间**: 2026-09-13T10:22:06Z
- **提交信息**: [Unified Cache][7/N]  Support MTP, EAGLE, and DSpark draft KV caches in the external linker (#37914)

Co-authored-by: hzh0425 <hzh0425@apache.org>

### [cebca69](https://github.com/sgl-project/sglang/commit/cebca698e2da89b73599bf358f3fb918c41fc2a6)

- **作者**: Jimmy Shong
- **时间**: 2026-09-13T08:23:41Z
- **提交信息**: [Qwen3.8] Enable NVIDIA NVFP4 on DGX Spark with file-backed PLE and PDL router fix (#39126)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: rdxa <rdxa@rdxa-int-spark-01.yvb.moe>
Co-authored-by: Yangmin Li <yangminl@nvidia.com>
Co-authored-by: Manrique <nanomlm@gmail.com>
Co-authored-by: yhyang201 <yhyang201@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
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


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91654
- **最后更新**: 2026-09-13T23:42:20Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 17
- **主要提交者**: Kevin H. Luu, Taneem Ibrahim, Jiangyun Zhu

## AI分析总结

# vLLM 昨日提交分析总结（共22条）

## 1. 主要更新类型分布

- **性能优化（约6条）**：EPD Python代理序列化开销削减、FP8虚拟初始化冗余转换消除、ROCm MiniMax M3标量上传去阻塞、DeepSelect TopK集成DSA稀疏索引器、Engram异步预取等。
- **Bug修复（约8条）**：DCP索引器交错映射、混合KV缓存加载报错、NVFP4权重NaN哨兵检测、Gemma4图像/视频预处理参数隔离、EPD多模态UUID保留等。
- **功能新增（约4条）**：多模态前缀注意力Triton/FlashInfer组合、DeepSeek-V4 Flash Vision的LoRA支持、NIXL PCP生产者KV分片暴露、Pooling评分API实际token用量上报。
- **测试与CI（约4条）**：VLM批不变性测试、V2 QSA runner warmup注册、NIXL传输几何fixture修复、XPU JIT warmup修复。

## 2. 关键变更点与项目方向的关系

- **并行策略深化**：围绕PCP/DCP（流水线/数据并行上下文）的KV gather映射、NIXL传输rank、Engram DP分片等，说明vLLM正持续强化大规模分布式推理下的KV缓存管理与跨节点传输能力。
- **稀疏注意力与多模态融合**：DSA稀疏索引器引入DeepSelect TopK、多模态前缀注意力组合内核，契合vLLM"高吞吐、低延迟服务"的核心目标。
- **新模型快速适配**：Gemma4去JIT化、DeepSeek-V4 Flash Vision LoRA、MiniMax M3 ROCm优化，体现对前沿模型生态的紧密跟进。
- **EPD（编码-预填充-解码分离）架构打磨**：序列化开销与UUID保留的修复，表明EPD正从实验走向生产可用。

## 3. 对项目的影响与潜在意义

- 性能类提交直接降低服务延迟与CPU/GPU开销，巩固vLLM在"cheap serving"上的竞争力。
- 大量Bug修复（尤其KV缓存、量化权重、多模态预处理）提升生产环境稳定性，减少静默错误风险。
- 测试与CI完善（批不变性、warmup注册）为后续重构提供回归保障，降低引入回归的概率。
- LoRA与新模型支持扩展了vLLM的适用场景，利于社区生态增长。

## 4. 值得关注的技术点

- **NaN哨兵检测NVFP4未加载权重**：一种巧妙的量化安全机制，值得借鉴。
- **DeepSelect TopK用于DSA稀疏索引**：稀疏注意力与TopK选择结合，可能成为长上下文推理的关键优化。
- **Engram异步预取与DP分片**：面向卸载式查找的异步化，暗示vLLM在内存层级管理上的新探索。
- **多模态前缀注意力组合内核**：Triton与FlashInfer协同，体现内核层面的异构调度思路。

## 5. 结合README背景的项目发展影响

vLLM定位为"Easy, fast, and cheap LLM serving for everyone"。本批提交从三个维度支撑该定位：**fast**——性能优化与稀疏注意力内核；**cheap**——EPD分离、KV缓存与量化效率提升；**everyone**——新模型、LoRA、多模态与ROCm/XPU多硬件覆盖。整体看，项目正从"单机高吞吐"向"分布式、多模态、多硬件、生产级稳定"演进，EPD与PCP/DCP相关提交的密集出现，标志着vLLM正在为超大规模、异构部署场景打基础。

## 详细提交记录

### [319cc5e](https://github.com/vllm-project/vllm/commit/319cc5ef19946d34c2e66cbbec5bda29d0bfa328)

- **作者**: Tianyu Guo
- **时间**: 2026-09-13T22:07:12Z
- **提交信息**: [Performance][EPD] Reduce Python proxy serialization overhead (#56657)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>

### [b234330](https://github.com/vllm-project/vllm/commit/b23433088bf29980d20dff1bd64c753dd8883506)

- **作者**: stu-cao
- **时间**: 2026-09-13T20:56:28Z
- **提交信息**: [Attention] Remove DCP indexer interleave guard and test TP1 output parity (#55802)

Signed-off-by: Stu Cao <stucao@Stus-MacBook-Pro.local>
Signed-off-by: <>
Signed-off-by: Summer Yang <girasoleyang@gmail.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Stu Cao <stucao@Stus-MacBook-Pro.local>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [186a1e6](https://github.com/vllm-project/vllm/commit/186a1e62221c02cdf8ef0433eb4ad33d1b48c7f7)

- **作者**: Roberto L. Castro
- **时间**: 2026-09-13T20:47:21Z
- **提交信息**: [Warmup] Gemma 4 de-JITification (#55768)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [586f652](https://github.com/vllm-project/vllm/commit/586f652f8d9e841901c40634c024a2ebbfe3402f)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-13T20:45:17Z
- **提交信息**: [Bugfix][PCP][DCP] Respect interleave in indexer KV gather mapping (#56715)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [7fe8fc8](https://github.com/vllm-project/vllm/commit/7fe8fc803d904795fd10b785776e20181aee64c5)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-13T20:23:15Z
- **提交信息**: [NIXL][PCP][DCP] Expose PCP producer KV shards as transfer ranks (#56645)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [71888f5](https://github.com/vllm-project/vllm/commit/71888f507ad5df5af2fae2ab39a6c1b0cc465eb1)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-13T19:06:13Z
- **提交信息**: [Perf] Avoid redundant conversions in FP8 dummy initialization (#56688)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [b6e2aa7](https://github.com/vllm-project/vllm/commit/b6e2aa748b2bef8d72f2003cd881a77ac47dcb57)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-13T17:34:09Z
- **提交信息**: [CI] Initialize warmup registry in V2 QSA runner fixture (#56707)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [dec0b5d](https://github.com/vllm-project/vllm/commit/dec0b5d63fc42dc1d1789caf572195c73dd86ea6)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-13T17:05:29Z
- **提交信息**: [Bugfix] Skip Triton autotune inspection without Triton (#56676)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [f09c52a](https://github.com/vllm-project/vllm/commit/f09c52a587f205963d3a2b8f1c42820a831ee4b0)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-13T16:56:02Z
- **提交信息**: [ROCm][Performance] Avoid blocking MiniMax M3 scalar upload (#56170)

Signed-off-by: fai <fangzhouai@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b7e0cda](https://github.com/vllm-project/vllm/commit/b7e0cdac5d11e3a1b32745079cf5591a685aa721)

- **作者**: Pavel Zakharov
- **时间**: 2026-09-13T14:58:09Z
- **提交信息**: [Bugfix] Detect unloaded NVFP4 weight scales with a NaN sentinel (#52501)

Signed-off-by: pavelzak <pavel.zakharov@gmail.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [82a85dc](https://github.com/vllm-project/vllm/commit/82a85dc1d2d5b3ad4453eaa1bd7596de888a66b3)

- **作者**: Matthew Bonanni
- **时间**: 2026-09-13T14:29:41Z
- **提交信息**: [Attention] Add Triton/FlashInfer composite for multimodal prefix attention (#56305)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [8cf9de9](https://github.com/vllm-project/vllm/commit/8cf9de9080ea5cded1c93e3d9a5ac531da0c93b6)

- **作者**: Shenglei Fu
- **时间**: 2026-09-13T14:22:03Z
- **提交信息**: [Test][Determinism] Cover VLM batch invariance in default execution mode (#56528)

Signed-off-by: Shenglei Fu <sfu@confluent.io>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [dd4c841](https://github.com/vllm-project/vllm/commit/dd4c8410707bdb833b155ff3258ce5271c0f476e)

- **作者**: linitra24
- **时间**: 2026-09-13T14:10:54Z
- **提交信息**: [LoRA] Add LoRA support for DeepSeek-V4 Flash Vision (#55897)

Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>

### [de50029](https://github.com/vllm-project/vllm/commit/de500290ffffeb7bd834872c0dea5331590dd40d)

- **作者**: liuzhenwei
- **时间**: 2026-09-13T13:44:24Z
- **提交信息**: [XPU][CI] fix jit_warmup_triton_launcher (#56670)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [2e9f7bb](https://github.com/vllm-project/vllm/commit/2e9f7bb45475c7e461079284a73ec9c53761c6b5)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-13T13:20:21Z
- **提交信息**: [Pooling] Report actual input token usage for scoring APIs (#56573)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [c351fd3](https://github.com/vllm-project/vllm/commit/c351fd3c649569d8a585eb22cfaf2ee728e5fc22)

- **作者**: Kebe
- **时间**: 2026-09-13T13:03:05Z
- **提交信息**: [Core] Fix ValueError on KV load failure with a hybrid KV cache (#50388)

Signed-off-by: Kebe <mail@kebe7jun.com>

### [fa1b3b1](https://github.com/vllm-project/vllm/commit/fa1b3b1922ccb2d7a597925765c4bec7f358d748)

- **作者**: Tianyu Guo
- **时间**: 2026-09-13T10:08:30Z
- **提交信息**: [Bugfix][EPD] Preserve explicit multimodal UUIDs with caches disabled (#56432)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>

### [d2d649e](https://github.com/vllm-project/vllm/commit/d2d649e674c75425d2d6975c87eb89fd4d55fff8)

- **作者**: Juntian Liu
- **时间**: 2026-09-13T09:44:23Z
- **提交信息**: [DS V4.1][Engram] Support async prefetch for offloaded engram lookups and engram DP sharding (#56512)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: ywang96 <>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [e7a3963](https://github.com/vllm-project/vllm/commit/e7a3963339654aa18b713f9ff233f129af9c7c8b)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-13T09:23:20Z
- **提交信息**: [Bugfix] Avoid repeated dummy initialization and random CPU Engram fills (#56682)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [a987777](https://github.com/vllm-project/vllm/commit/a987777755c83863b5d563c15630dd324033d53f)

- **作者**: Ylean
- **时间**: 2026-09-13T09:07:12Z
- **提交信息**: [Bugfix][Gemma4] Keep image kwargs out of video preprocessing (#56652)

Signed-off-by: Ylean <61880605+Woolgathererer@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [fa008bd](https://github.com/vllm-project/vllm/commit/fa008bdccf10f2f31f84553112a227cf1b8947d7)

- **作者**: Jiangyun Zhu
- **时间**: 2026-09-13T07:44:37Z
- **提交信息**: [Perf][Kernel] Integrate DeepSelect TopK for the DSA sparse indexer (#56464)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Roger Wang <hey@rogerw.io>
Co-authored-by: Kimi Code <noreply@moonshot.ai>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [1cfd972](https://github.com/vllm-project/vllm/commit/1cfd9728166c73747acdb423e7a49b23f27cdc44)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-13T07:36:06Z
- **提交信息**: [CI] Fix NIXL transfer-rank geometry fixture (#56672)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-14
**监控日期**: 2026-09-13
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6782
- **最后更新**: 2026-09-13T22:21:10Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Qi Jia, linzhenpl07, Yuan Wu

## AI分析总结

## 一、主要更新类型

本批次共 4 个提交，覆盖多个方向：

- **功能新增**：NIXL omni connector（#6093）、session-owned streaming VAE decode（#6533）
- **性能优化**：前端内存图像响应分块传输（#7459）
- **文档/适配更新**：NPU 平台 MiniMax-H3 INT8 DLO 保留 AllGather（#7444）

整体呈现“新硬件后端接入 + 多模态推理链路优化”的组合特征。

## 二、关键变更点与项目方向的关系

- **NIXL omni connector**：引入 NIXL 作为新的 KV/数据传输连接器，属于核心通信层扩展，契合 vLLM-Omni 面向“omni-modality 模型服务”的定位，为跨节点、跨设备高效传输提供新选项。
- **Streaming VAE decode（AR-Diffusion）**：为自回归扩散场景加入会话级流式 VAE 解码，直接服务于图像/视频生成类多模态模型的低延迟输出，是推理链路端到端优化的重要一环。
- **前端图像响应分块**：将内存中的图像文件响应改为 chunked 传输，降低大图返回时的内存峰值与首字节延迟，属于服务端 I/O 体验优化。
- **NPU MiniMax-H3 INT8 文档更新**：明确在特定量化配置下保留 AllGather，体现对国产 NPU 平台与量化推理的持续适配。

## 三、对项目的影响与潜在意义

- NIXL connector 的加入提升了项目在分布式/异构硬件上的可扩展性，为后续多后端统一传输层打下基础。
- 流式 VAE 解码使 AR-Diffusion 类模型具备更平滑的生成体验，增强项目在生成式多模态场景的竞争力。
- 前端分块响应虽是小改动，但直接改善 API 服务在大图像场景下的稳定性与资源占用。
- NPU 相关文档更新表明项目在国产加速卡生态上的投入在持续，有利于吸引更广泛的部署用户。

## 四、值得关注的技术点

- NIXL 与现有连接器（如 NCCL、Mooncake 等）的协作与切换机制。
- “session-owned”流式 VAE 解码的会话生命周期管理与显存/缓存复用策略。
- INT8 DLO 下保留 AllGather 的精度与性能权衡，是否会影响其他量化路径。
- 前端 chunked 响应与流式生成接口的协同，是否可进一步统一为端到端流式管线。

## 五、结合项目背景的发展影响

vLLM-Omni 定位为“易用、快速、低成本的全模态模型服务”。本批提交从**通信层（NIXL）、生成层（流式 VAE）、服务层（前端分块）、硬件适配层（NPU 文档）**四个维度同时推进，说明项目正从“支持多模态模型”走向“在多样硬件与部署形态下高效服务多模态模型”。这些改动共同强化了项目在分布式推理、生成式多模态和异构硬件兼容性上的能力，符合其面向“everyone”的普惠服务目标，也为后续统一多后端、多模态流式服务架构积累了关键组件。

## 详细提交记录

### [6505577](https://github.com/vllm-project/vllm-omni/commit/65055774596d53362ef8c8340ed155ff12cd0d54)

- **作者**: Lei Ke
- **时间**: 2026-09-13T22:20:59Z
- **提交信息**: [Doc][NPU] Keep AllGather for MiniMax-H3 INT8 DLO (#7444)

Signed-off-by: KrystalRay <keeleiray@gmail.com>
Co-authored-by: KrystalRay <keeleiray@gmail.com>

### [e284d90](https://github.com/vllm-project/vllm-omni/commit/e284d907b5554038bef6ab861bdb78b0b99dd5ea)

- **作者**: Qi Jia
- **时间**: 2026-09-13T12:33:10Z
- **提交信息**: [Perf][Frontend] Chunk in-memory image file responses (#7459)

Signed-off-by: QI JIA <qi.jia@shengshu.ai>
Co-authored-by: QI JIA <qi.jia@shengshu.ai>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [311e714](https://github.com/vllm-project/vllm-omni/commit/311e714d34be1c80714833abc754635aa3c1b59b)

- **作者**: linzhenpl07
- **时间**: 2026-09-13T10:17:11Z
- **提交信息**: [AR-Diffusion] Add session-owned streaming VAE decode (#6533)

Signed-off-by: linzhenpl07 <linzhenpl07@gmail.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [6753bbd](https://github.com/vllm-project/vllm-omni/commit/6753bbd18c9a1f45cfebcec3eacdd2f1e5ea859b)

- **作者**: Yuan Wu
- **时间**: 2026-09-13T08:35:02Z
- **提交信息**: [Core] Add NIXL omni connector (#6093)

Signed-off-by: yuanwu <yuan.wu@intel.com>
Signed-off-by: Yuan Wu <yuan.wu@intel.com>

---
