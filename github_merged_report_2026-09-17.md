# GitHub Stars 合并报告 - 2026-09-17

**合并日期**: 2026-09-18
**监控日期**: 2026-09-17
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


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2214
- **最后更新**: 2026-09-17T05:15:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2825
- **最后更新**: 2026-09-17T19:41:03Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: Qin-sx, Bilang ZHANG, Xin Qiu

## AI分析总结

## 一、主要更新类型

本批 5 条提交以**功能新增**和**性能优化**为主，辅以一次**重构**：

- 功能新增：Flux2 的 PipeFusion 流水线并行（#1268）、SwiftVR 多 GPU chunk 并行（#1525）、SeedVR 按请求尺寸与目标尺寸匹配（#1523）。
- 性能优化：Intel XPU 上 MiniMax-H3 VAE 的 CUTE attention 优化（#1521）。
- 重构/移除：删除 wan2.2_audio 支持（#1522）。

## 二、关键变更点与项目方向

- **Flux2 PipeFusion**：新增 `common/distributed` 流水线并行基础设施（P2P 通信管理、运行时状态）与 Flux2 专用驱动，支持多 GPU 分阶段推理，并引入跨 patch 的 stale-KV 缓存。这与 LightX2V 作为“轻量视频生成推理框架”的核心定位高度一致——持续扩展多卡并行能力。
- **SwiftVR chunk 并行**：为视频推理加入多 GPU 分块并行并优化推理流程，进一步丰富并行策略矩阵。
- **SeedVR 尺寸控制**：支持按请求指定尺寸并匹配目标尺寸，提升推理灵活性。
- **移除 wan2.2_audio**：精简模型支持面，聚焦主线视频生成能力。
- **XPU CUTE attention**：针对 Intel XPU 的 VAE 注意力内核优化，扩展硬件后端覆盖。

整体方向：**多 GPU 并行 + 多硬件后端 + 推理灵活性**，同时做减法清理边缘功能。

## 三、对项目的影响与潜在意义

- PipeFusion 使 Flux2 从单卡走向多卡流水线推理，据对比数据，PP8 总耗时约 21.5s，远优于 USP8 的约 196s，**数量级提升推理效率**，对长视频/大模型部署意义重大。
- 多后端（XPU）与多并行策略（chunk、pipeline）的积累，强化了框架的**通用性与可移植性**，有利于吸引不同硬件生态的用户。
- 移除 wan2.2_audio 表明项目在**收敛维护成本**，把资源集中到核心视频生成路径。

## 四、值得关注的技术点

- **stale-KV 缓存**：图像 KV 跨 patch 复用，非首阶段复用 patch 0 的文本编码隐状态（stale-text 近似），是精度与效率的权衡设计。
- **异步流水线**：warmup 用同步、主循环用异步，实现 per-patch 计算与通信重叠。
- **预分配 recv buffer + FIFO 任务队列 + 异步 prefetch** 的 P2P 通信管理，是流水线性能的关键。
- **XPU CUTE 内核**的尾掩码（tail masking）修复，体现对边界正确性的关注。

## 五、结合项目背景的发展影响

LightX2V 定位为轻量视频生成推理框架，本批提交延续其“**高效、多卡、多后端**”的技术路线：PipeFusion 与 chunk 并行补齐了并行推理能力版图，XPU 优化拓宽硬件适配，SeedVR 尺寸控制增强实用性，而移除 audio 支持则体现聚焦。整体上，这些提交推动框架从“能推理”向“**高效、可扩展、跨硬件**”的生产级推理框架演进，巩固其在视频生成推理领域的竞争力。

## 详细提交记录

### [69018c9](https://github.com/ModelTC/LightX2V/commit/69018c92b0a42d9b0cf962a248fadbfe0cbc03de)

- **作者**: Qin-sx
- **时间**: 2026-09-17T12:10:50Z
- **提交信息**: feat: support pipefusion for flux2 (#1268)

# Support PipeFusion parallel inference for Flux2

## Summary

Adds pipeline parallelism (PipeFusion) support for the Flux2 model in
LightX2V, enabling multi-GPU inference with per-patch stale-KV caching
across pipeline stages.

## Key Components

### New modules

- **`lightx2v/common/distributed/`** — pipeline parallel infrastructure:
- `pipeline_comm.py` (`PipelineComm`): P2P communication manager between
adjacent stages. Wraps `dist.isend`/`dist.irecv` with pre-allocated recv
buffers, a FIFO task queue, and async `recv_next()` prefetch.
- `pipeline_state.py` (`PipelineRuntimeState`): patch metadata
management and stage-identification helpers (`is_pipeline_first_stage`,
`get_pipeline_parallel_rank`, etc.).
- **`lightx2v/models/networks/flux2/infer/pipefusion/`** — Flux2
PipeFusion driver:
- `pipeline_driver.py` (`Flux2PipelineDriver`): orchestrates the
denoising loop across stages — sync pipeline for warmup, async pipeline
for the main loop with per-patch compute/comm overlap.
- `transformer_infer.py` (`Flux2PipeFusionTransformerInfer`): subclasses
`Flux2TransformerInfer` to run only the current stage's block subset and
apply stale-KV caching(image KV cached across patches; on non-first
stages the encoder hidden states are reused from patch 0 — a stale-text
approximation).

## Comparison

| Stage | PP8 | USP8 |
|---|---|---|
| Load models | 11.55 ~ 13.36s | 46.69 ~ 54.62s |
| Run Text Encoder | 0.46 ~ 0.51s | 18.49 ~ 21.49s |
| Run Encoders (incl. text encoder) | 0.73 ~ 0.82s | 18.83 ~ 21.81s |
| Run DiT | 6.62 ~ 8.51s | 112.71 ~ 122.66s |
| RUN pipeline (excl. load, incl. VAE) | 7.94 ~ 9.60s (normal
ranks)<br>10.72s (rank7, slowest) | 134.39 ~ 141.67s (normal
ranks)<br>142.46s (rank7, slowest) |
| Run VAE Decoder | 0.45s (rank7) | 0.65 ~ 0.74s |
| Total Cost (incl. model load) | 21.52 ~ 21.63s (normal
ranks)<br>22.81s (rank7, slowest) | 195.67 ~ 195.85s (normal
ranks)<br>196.11s (rank0, slowest) |

### PP
```json
{
  "model_cls": "flux2",
  "model_variant": "klein",
  "task": "t2i",
  "infer_steps": 20,
  "sample_guide_scale": 1.0,
  "vae_scale_factor": 16,
  "feature_caching": "None",
  "enable_cfg": false,
  "patch_size": 2,
  "tokenizer_max_length": 512,
  "rope_type": "flashinfer_rope",
  "attn_type": "flash_attn2",
  "max_custom_size": 2048,
  "parallel": {
    "cfg_p_size": 1,
    "seq_p_size": 1,
    "pp_size": 8,
    "num_pipeline_patch": 8,
    "pipeline_warmup_steps": 3
  }
}


```

```bash
torchrun --nproc_per_node=8 -m lightx2v.infer \
    --model_cls flux2 \
    --task t2i \
    --target_shape 1024 1024 \
    --model_path $model_path \
    --prompt "A cat running in a garden" \
    --save_result_path "save_results/flux2_klein_pp8.png" \
    --config_json "${lightx2v_path}/configs/flux2/flux2_pp8.json" \
    2>&1 | tee "$log_file"
```

<img width="1024" height="1024" alt="flux2_klein_pp8"
src="https://github.com/user-attachments/assets/959c295a-aab2-4961-8dd8-c3bb40bd9d25"
/>



### USP
```json
{
  "model_cls": "flux2",
  "model_variant": "klein",
  "task": "t2i",
  "infer_steps": 20,
  "sample_guide_scale": 1.0,
  "vae_scale_factor": 16,
  "feature_caching": "None",
  "enable_cfg": false,
  "patch_size": 2,
  "tokenizer_max_length": 512,
  "rope_type": "flashinfer_rope",
  "attn_type": "flash_attn2",
  "max_custom_size": 2048,
  "cpu_offload": true,
  "offload_granularity": "block",
  "use_event_offload": true,
  "offload_use_block_slab": true,
  "parallel": {
    "seq_p_size": 8,
    "seq_p_attn_type": "ulysses"
  }
}

```

```bash
torchrun --nproc_per_node=8 -m lightx2v.infer \
    --model_cls flux2 \
    --task t2i \
    --target_shape 1024 1024 \
    --model_path $model_path \
    --prompt "A cat running in a garden" \
    --save_result_path "save_results/flux2_klein_usp8.png" \
    --config_json "${lightx2v_path}/configs/flux2/flux2_usp8.json" \
    2>&1 | tee "$log_file"
```

<img width="1024" height="1024" alt="flux2_klein_usp8"
src="https://github.com/user-attachments/assets/1ab3a466-319d-43ff-a6a7-1aad60889c50"
/>

## Pipefusion Test
```bash
torchrun --nproc_per_node=8 -m lightx2v.server \
    --model_cls flux2 \
    --task t2i \
    --model_path "$model_path" \
    --config_json "${lightx2v_path}/configs/flux2/flux2_klein_pipefusion.json" \
    --host 0.0.0.0 \
    --port $port \
    > "$server_log" 2>&1 &
server_pid=$!
echo "server started (pid=$server_pid), log: $server_log"

python3 "${script_dir}/repeat_server_client.py" \
    --port $port \
    --prompt "A cat running in a garden" \
    --prompt_b "A snowy mountain at sunset" \
    --size 1024 1024 \
    --seed 42 \
    --save_result_path "${script_dir}/save_results/flux2_klein_pp8_server.png"

kill $server_pid 2>/dev/null
wait $server_pid 2>/dev/null
echo "server stopped"
```

```python
"""
Runs ALL tests sequentially on the same resident server:
  item 1: same prompt twice -> outputs must be identical.
  item 2: B-baseline vs B-after-A must be identical (prompt A must not pollute B).
  item 3: change resolution and request again -> must complete and stay
          deterministic (shape-dependent buffers must be reallocated, not stale).
  item 4: after an interrupted/cancelled request, the next request must still run.
Exit code 0 only if all pass.
"""

import argparse
import hashlib
import os
import time

import requests


def wait_ready(base, timeout=600):
    url = f"{base}/v1/service/status"
    t0 = time.monotonic()
    while time.monotonic() - t0 < timeout:
        try:
            if requests.get(url, timeout=3).status_code == 200:
                return
        except requests.RequestException:
            pass
        time.sleep(2)
    raise RuntimeError("server did not become ready in time")


def submit_only(base, payload):
    """POST a task and return its task_id without waiting for completion."""
    r = requests.post(f"{base}/v1/tasks/image/", json=payload, timeout=30)
    r.raise_for_status()
    return r.json()["task_id"]


def wait_done(base, task_id, timeout=600):
    t0 = time.monotonic()
    while time.monotonic() - t0 < timeout:
        s = requests.get(f"{base}/v1/tasks/{task_id}/status", timeout=10).json()
        status = s.get("status")
        if status == "completed":
            return task_id
        if status in ("failed", "cancelled"):
            raise RuntimeError(f"task {task_id} {status}: {s.get('error')}")
        time.sleep(1)
    raise RuntimeError(f"task {task_id} timed out")


def submit_and_wait(base, payload, timeout=600):
    return wait_done(base, submit_only(base, payload), timeout)


def wait_until_processing(base, task_id, timeout=120):
    """Return once the task leaves the pending queue (processing/terminal)."""
    t0 = time.monotonic()
    while time.monotonic() - t0 < timeout:
        status = requests.get(f"{base}/v1/tasks/{task_id}/status", timeout=10).json().get("status")
        if status in ("processing", "completed", "failed", "cancelled"):
            return status
        time.sleep(0.3)
    return None


def cancel(base, task_id):
    requests.delete(f"{base}/v1/tasks/{task_id}", timeout=10)


def md5(path):
    with open(path, "rb") as f:
        return hashlib.md5(f.read()).hexdigest()


def test_item1_determinism(base, mk_payload, stem, ext):
    """item 1: same prompt twice -> outputs must be identical."""
    path1 = f"{stem}_item1_req1{ext}"
    path2 = f"{stem}_item1_req2{ext}"
    print("\n########## [item1] same-prompt determinism ##########")
    print("===== [item1] request 1 (prompt A) =====")
    submit_and_wait(base, mk_payload("A", path1))
    print(f"request 1 done -> {path1}")
    print("===== [item1] request 2 (prompt A) =====")
    submit_and_wait(base, mk_payload("A", path2))
    print(f"request 2 done -> {path2}")

    h1, h2 = md5(path1), md5(path2)
    print(f"[item1] req1 md5={h1}")
    print(f"[item1] req2 md5={h2}")
    ok = h1 == h2
    print("[item1] PASS: two requests produced identical output" if ok else "[item1] DIFFER: possible stale-state leak between requests")
    return ok


def test_item2_pollution(base, mk_payload, stem, ext):
    """item 2: running prompt A first must not pollute a later prompt B."""
    b_base = f"{stem}_item2_B_baseline{ext}"
    a_mid = f"{stem}_item2_A{ext}"
    b_test = f"{stem}_item2_B_after_A{ext}"
    print("\n########## [item2] cross-prompt pollution ##########")
    print("===== [item2] baseline: prompt B as the first request =====")
    submit_and_wait(base, mk_payload("B", b_base))
    print(f"baseline done -> {b_base}")
    print("===== [item2] intervening: prompt A =====")
    submit_and_wait(base, mk_payload("A", a_mid))
    print(f"prompt A done -> {a_mid}")
    print("===== [item2] test: prompt B after prompt A =====")
    submit_and_wait(base, mk_payload("B", b_test))
    print(f"prompt B (after A) done -> {b_test}")

    hb, ht = md5(b_base), md5(b_test)
    print(f"[item2] B_baseline md5={hb}")
    print(f"[item2] B_after_A  md5={ht}")
    ok = hb == ht
    print("[item2] PASS: prompt B is identical with/without a prior prompt A (no pollution)" if ok else "[item2] DIFFER: prompt B changed after prompt A -> cross-request state pollution")
    return ok


def test_item3_resolution(base, mk_payload, stem, ext, base_size, alt_size):
    """item 3: change resolution across requests."""
    p0 = f"{stem}_item3_base{ext}"            # e.g. 1024
    p1 = f"{stem}_item3_alt_after_base{ext}"  # alt right after base (the change)
    p2 = f"{stem}_item3_alt_steady{ext}"      # alt after alt (baseline)
    print(f"\n########## [item3] resolution change {base_size} -> {alt_size} ##########")
    print(f"===== [item3] request 0 (base size {base_size}) =====")
    submit_and_wait(base, mk_payload("A", p0, size=base_size))
    print(f"base-size request done -> {p0}")
    print(f"===== [item3] request 1 (alt size {alt_size}, right after base) =====")
    submit_and_wait(base, mk_payload("A", p1, size=alt_size))
    print(f"alt-after-base done -> {p1}")
    print(f"===== [item3] request 2 (alt size {alt_size}, steady) =====")
    submit_and_wait(base, mk_payload("A", p2, size=alt_size))
    print(f"alt-steady done -> {p2}")

    h1, h2 = md5(p1), md5(p2)
    print(f"[item3] alt_after_base md5={h1}")
    print(f"[item3] alt_steady     md5={h2}")
    ok = h1 == h2
    print("[item3] PASS: resolution change runs and leaves no stale shape-dependent state" if ok else "[item3] DIFFER: resolution change polluted by stale shape-dependent state")
    return ok


def test_item4_recover_after_cancel(base, mk_payload, stem, ext):
    """item 4: after an interrupted request, the next request must run."""
    interrupted = f"{stem}_item4_interrupted{ext}"
    recovered = f"{stem}_item4_recovered{ext}"
    print("\n########## [item4] recover after interrupted request ##########")
    tid = submit_only(base, mk_payload("A", interrupted))
    status = wait_until_processing(base, tid)
    print(f"[item4] interrupted task {tid} reached status={status}, cancelling")
    cancel(base, tid)

    print("===== [item4] next request after cancel =====")
    try:
        submit_and_wait(base, mk_payload("B", recovered))
    except Exception as e:
        print(f"[item4] DIFFER: next request failed after a cancelled one -> {e}")
        return False
    print(f"[item4] recovered request done -> {recovered}")
    print("[item4] PASS: server still serves requests after an interrupted one")
    return True


def main():
    ap = argparse.ArgumentParser()
    ap.add_argument("--port", type=int, default=8000)
    ap.add_argument("--prompt", type=str, default="A cat running in a garden", help="prompt A")
    ap.add_argument("--prompt_b", type=str, default="A snowy mountain at sunset", help="prompt B for the pollution test (item 2); must differ from --prompt")
    ap.add_argument("--size", type=int, nargs="+", default=None, help="default resolution: HEIGHT WIDTH")
    ap.add_argument("--alt_size", type=int, nargs="+", default=[1536, 1536], help="alternate resolution for item 3: HEIGHT WIDTH")
    ap.add_argument("--seed", type=int, default=42)
    ap.add_argument("--save_result_path", type=str, required=True)
    args = ap.parse_args()

    if args.prompt_b == args.prompt:
        raise SystemExit("--prompt_b must differ from --prompt for the item-2 pollution test")

    base = f"http://127.0.0.1:{args.port}"
    stem, ext = os.path.splitext(args.save_result_path)
    prompts = {"A": args.prompt, "B": args.prompt_b}

    def mk_payload(which, path, size=None):
        p = {"task": "t2i", "prompt": prompts[which], "seed": args.seed, "save_result_path": path}
        chosen = size if size is not None else args.size
        if chosen:
            p["size"] = list(chosen)
        return p

    wait_ready(base)

    # Run all tests sequentially on the same resident server.
    ok1 = test_item1_determinism(base, mk_payload, stem, ext)
    ok2 = test_item2_pollution(base, mk_payload, stem, ext)
    ok3 = test_item3_resolution(base, mk_payload, stem, ext, args.size or [1024, 1024], args.alt_size)
    ok4 = test_item4_recover_after_cancel(base, mk_payload, stem, ext)

    print("\n########## summary ##########")
    print(f"item1 (same-prompt determinism): {'PASS' if ok1 else 'FAIL'}")
    print(f"item2 (cross-prompt pollution):  {'PASS' if ok2 else 'FAIL'}")
    print(f"item3 (resolution change):       {'PASS' if ok3 else 'FAIL'}")
    print(f"item4 (recover after cancel):    {'PASS' if ok4 else 'FAIL'}")
    raise SystemExit(0 if (ok1 and ok2 and ok3 and ok4) else 1)


if __name__ == "__main__":
    main()
```

```bash
########## summary ##########
item1 (same-prompt determinism): PASS
item2 (cross-prompt pollution):  PASS
item3 (resolution change):       PASS
item4 (recover after cancel):    PASS
server stopped
```

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [12c3f00](https://github.com/ModelTC/LightX2V/commit/12c3f00eccc7af2618728d05b39089ba3dc515df)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-17T11:52:21Z
- **提交信息**: feat(swiftvr): add multi-GPU chunk parallelism and optimize video inf… (#1525)

…erence

### [76856a8](https://github.com/ModelTC/LightX2V/commit/76856a84b97f5f4b035ccd8d2b98f8d1c567d36b)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-17T09:33:26Z
- **提交信息**: feat(seedvr): support per-request size and match_target_size (#1523)

### [62d99a7](https://github.com/ModelTC/LightX2V/commit/62d99a762b5ec5ddeebd9ea65fb71bf7dc38558d)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-17T08:52:58Z
- **提交信息**: refactor(wan): remove wan2.2_audio support (#1522)

### [1b9a33f](https://github.com/ModelTC/LightX2V/commit/1b9a33fa84c94fdf033af9c57d3bccd611a633df)

- **作者**: Xin Qiu
- **时间**: 2026-09-17T08:23:21Z
- **提交信息**:  perf(xpu): add CUTE attention optimization for MiniMax-H3 VAE (#1521)

## Summary

This PR adds an Intel XPU-specific CUTE attention implementation for the
MiniMax-H3 Video VAE.

  ## Changes

- Add a CUTE D64 attention kernel for MiniMax-H3 Video VAE on Intel XPU
  - Isolate the VAE CUTE kernel build and fix tail masking behavior
 
 ## Usage
Enable the backend through `vae_attn_type: minimax_h3_xpu_cute`

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2251
- **最后更新**: 2026-09-17T14:40:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6437
- **最后更新**: 2026-09-18T00:18:13Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 9
- **主要提交者**: Daniel Stokes, Alex Yang, summer

## AI分析总结

# FlashInfer 昨日提交总结

## 一、主要更新类型

昨日共 9 个提交，涵盖功能新增、性能优化、Bug 修复与工程改进四类。功能方面，集成 MXFP8×BF16 MegaMOE（#4604），并推出实验性 SM110 GQA decode 预编译 API（#5302）。性能方面，针对 SM107 调优 nvfp4/mxfp4/mxfp8 量化内核调度并引入 128x4 tile 内核（#5300）；同时为 TRT-LLM MoE 中间量化环节启用 PDL（#5281）。修复方面涉及 cute-dsl ragged prefill、FA2 prefill 临时缓冲分配、KDA WY decode 及 CLI 安装流程等（#4816、#5177、#5253、#5299）。工程侧则在 CUTLASS DSL 低于 4.7 时跳过相关测试（#5215）。

## 二、关键变更与项目方向

新硬件适配密集：SM100（Blackwell）、SM107（Rubin）、SM110（Thor）均有针对性工作，显示项目快速跟进 NVIDIA 新架构。量化与 MoE 是核心战场，MXFP8/MXFP4/NVFP4 内核与 MegaMOE 集成直接服务低精度推理与专家并行。PDL 优化从单 kernel 扩展至端到端流水线，覆盖 FC1→量化→FC2 串联链路。稳定性方面，多处修复聚焦 GQA、CUDA Graph、workspace 溢出与依赖版本门控，体现对生产可用性的重视。

## 三、项目影响与潜在意义

#5177 修复 GQA 下 workspace 膨胀（72.7GB→2.3GB），直接解决 vLLM 启动失败，对下游集成意义重大。#4604 打通混合精度 MoE，配合 SGLang 下游 PR 强化端到端链路。#5302 支持 CUDA Graph 重放，报告最高 52% 延迟下降。#5281 降低 MoE 推理延迟，提升 TRT-LLM 集成竞争力。#5253、#4816 消除 SM107 硬故障与未初始化内存返回，提升鲁棒性。

## 四、值得关注的技术点

128x4 tile 布局将 scale 写入合并为连续 512B 全行存储，减少 cache line 分裂；SM110 GQA 内核采用 `tcgen05.mma`、TMA、TMEM，代表最新 Tensor Core 编程范式；通过 CPU 镜像在 host 侧决策空 KV 行填充，保持 CUDA Graph 可捕获性；明确拒绝抬高 CUTLASS DSL 版本下限，改用运行时门控以避免依赖冲突。PDL 与依赖等待共存、CUDA Graph 重放兼容性及固定 tactic 等价性测试，为后续推广提供范式。

## 五、结合项目定位的发展意义

FlashInfer 定位为“High-Performance GPU Kernels for Inference”。本批提交延续该方向：一方面扩展新架构与新精度覆盖，巩固内核性能领先；另一方面密集修复下游框架实际遇到的显存与兼容问题。项目正从“内核库”向“生产级推理后端”演进，生态协同与工程稳健性成为与性能同等重要的竞争力。

## 详细提交记录

### [aa7c67f](https://github.com/flashinfer-ai/flashinfer/commit/aa7c67f2b876b89be34c7a70ac022369a56e60d5)

- **作者**: Daniel Stokes
- **时间**: 2026-09-17T23:47:00Z
- **提交信息**: feat(moe_ep): MXFP8 x BF16 integration (#4604)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Adds support for SM100 MXFP8 x BF16 MegaMOE to flashinfer

## 🔍 Related Issues

<!-- Link any related issues here -->

https://github.com/flashinfer-ai/flashinfer/issues/3781

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
Downstream PR demonstrating framework integration:
https://github.com/sgl-project/sglang/pull/35459/commits

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added Blackwell MegaMoE support for BF16 activations with MXFP8 E4M3
and E5M2 weights.
* Added weight preprocessing, validation, autotuning, workspace pooling,
distributed execution, and BF16 output support.
* Exposed mixed-precision configuration, runtime requirements, reference
computation, and launch utilities through the public API.

* **Documentation**
* Expanded tuning guidance and clarified configuration and
preprocessed-weight usage.

* **Tests**
* Added functional and integration coverage for execution,
preprocessing, autotuning, distributed operation, and workspace reuse.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [bbf39c5](https://github.com/flashinfer-ai/flashinfer/commit/bbf39c559d3f4b09482c014e710a3402a67fef88)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-17T23:28:08Z
- **提交信息**: perf(quantization): SM107 dispatch tuning and 128x4 tile kernels for nvfp4/mxfp4/mxfp8 (#5300)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Tunes the CuTe-DSL quantization kernels (`nvfp4_quantize`,
`mxfp4_quantize`, `mxfp8_quantize`) for SM107. Every change is gated on
`get_compute_capability() == (10, 7)`; SM100/SM103 dispatch and codegen
are unchanged.

- **128x4 tile kernels** (one per quantizer). In the row-based kernels a
warp owns one row, so its 1-byte scale stores in the 128x4 layout touch
8 different 128 B lines per 32 SF blocks. A CTA now quantizes a 128-row
× 4-column tile whose scales are one contiguous 512 B block, stages them
in shared memory, and writes them back with full-line stores. Loads stay
coalesced; output is byte-identical to the row kernels. Used for wide
inputs (M ≥ 1024, K ≥ 2048, rows ≥ 8 KiB with ≥ 16 MiB input, or rows ≥
4 KiB with ≥ 64 MiB). The nvfp4 TMA kernel keeps precedence where it
applies.
- **nvfp4 vector path**: 2 persistent CTAs/SM for inputs ≥ 1M elements;
FP8 input pairs two strided SF blocks per thread (`pair_fp8_blocks`,
part of the kernel cache key, requested only for FP8) so each thread
keeps two 16 B loads in flight; TMA enabled for FP16/BF16 with
layout-specific crossovers.
- **mxfp8**: 256-thread "small blocks" kernel for wide rows (K > 16384
all dtypes, 8192 < K ≤ 12288 for 16-bit); lower persistent grid caps
(FP32 linear keeps the default). **mxfp4**: 2 CTAs/SM from 32M elements.

**Performance** on Rubin (SM107), speedup of this branch over `main`,
geomean over the swept shapes (1024×8192 to
8192×24576), cold L2:

| Config | linear | 8x4 | 128x4 |
|---|---|---|---|
| nvfp4 bf16 | 1.02x | 1.04x | 1.08x |
| nvfp4 fp16 | 1.02x | 1.04x | 1.09x |
| mxfp4 bf16 | 0.99x | 1.00x | 1.03x |
| mxfp4 fp16 | 0.99x | 1.00x | 1.03x |
| mxfp8 bf16 | 1.01x | 1.04x | 1.05x |
| mxfp8 fp16 | 1.01x | 1.04x | 1.05x |
| mxfp8 fp32 | 1.00x | 1.03x | 1.04x |

The 128x4 layout, which the GEMMs consume, gains the most; shapes below
the SM107 thresholds are unchanged by
construction.

<details>
<summary><b>Speedup plots (click to expand)</b></summary>

`nvfp4_quantize()`
<img width="1663" height="1481"
alt="nvfp4_bfloat16_swizzled_8x4_speedup"
src="https://github.com/user-attachments/assets/02055eb9-c7fe-493d-a31b-344846db9ce5"
/>

<img width="1663" height="1481"
alt="nvfp4_bfloat16_swizzled_128x4_speedup"
src="https://github.com/user-attachments/assets/e3f68269-89aa-4606-bb3c-9064c302fc6c"
/>

`mxfp4_quantize()`
<img width="1663" height="1481"
alt="mxfp4_bfloat16_swizzled_8x4_speedup"
src="https://github.com/user-attachments/assets/691c207a-d6ee-4b82-aa99-c427a3f209fe"
/>
<img width="1663" height="1481"
alt="mxfp4_bfloat16_swizzled_128x4_speedup"
src="https://github.com/user-attachments/assets/a2d8ef98-9e74-43aa-b3fc-2c7712fc62b9"
/>


`mxfp8_quantize()`
<img width="1663" height="1481"
alt="mxfp8_bfloat16_swizzled_8x4_speedup"
src="https://github.com/user-attachments/assets/b6bb4c6a-220d-483f-a38d-4b4e7e7eea2c"
/>
<img width="1663" height="1481"
alt="mxfp8_bfloat16_swizzled_128x4_speedup"
src="https://github.com/user-attachments/assets/eb36031f-5845-4775-8b7f-04b712725c41"
/>

</details>

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

* **Performance**
* Improved FP4 and FP8 quantization performance on SM107 GPUs through
optimized tile-based processing and workload routing.
  * Improved handling of large inputs, wide rows, and FP8 block pairing.
* Added configurable TMA selection for NVFP4 quantization through
`FLASHINFER_NVFP4_QUANTIZE_USE_TMA`.

* **Bug Fixes**
* Improved quantization handling for irregular dimensions, padded
layouts, and small inputs.

* **Tests**
* Expanded FP4 quantization coverage for edge-case shapes and layout
scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [fdc5634](https://github.com/flashinfer-ai/flashinfer/commit/fdc5634386f12378e4ffd9ae47a78f0110a63120)

- **作者**: eigen
- **时间**: 2026-09-17T22:57:34Z
- **提交信息**: feat(cake_gqa): add experimental prepared SM110 GQA decode (#5302)

## 📌 Description

Add an explicit prepared SM110 GQA decode API for repeated launches and
CUDA Graph replay. It reuses caller output and per-instance workspace,
while preserving the existing `sm110_gqa_decode` convenience API
unchanged.

The default routes are original short, B4/capacity256 N32 direct output
(zero global workspace), B1/capacity1024 N64 KV-last with ten splits,
and B1/capacity4096 N32 ring3 with ten splits. The optimized QK/PV
bodies use `tcgen05.mma`, TMA and TMEM. Other shapes fall back to
original long; explicit `num_splits=1` also keeps that route above
capacity64.

The generated kernel bodies are source-equivalent to the qualified
implementation, with mechanical symbol/include renames only. The new
manifest authenticates the added source closure. No AOT or automatic
backend routing changes are included.

The source study preserves all four original shapes (FP16, Hq=32, Hkv=8,
D=128) and reports **38.11% lower primary GPU latency** against the
pinned original under controlled partial KV reuse, **52.22% / 16.73%**
reductions on the two long shapes, and **32.70%** in the separate
ordinary-launch crosscheck. Hot candidate/XQA latencies are **11.144 /
13.376 us** and **21.816 / 37.792 us**.

Measured on aarch64 NVIDIA Thor with CUDA 13.4 and PyTorch
2.14.0a0+b2c75dd062.nvinternal.main, using strict CUPTI, six paired
groups of 32 retained samples, and matched observed GPC/EMC clocks of
1.386/3.2 GHz. The original is pinned to #5052 head
`223e0706c9398ec628d87a8a93ed1548efcd7900`; XQA uses a fixed cubin
specialization. The primary score aggregates nine cells: B4/cap256,
B1/cap1024 and B1/cap4096 crossed with producer-hot, recent-64 and
recent-256 KV conditioning. It uses geometric means of condition-level
paired ratios, not ratios of marginal medians.

Representative producer-hot GPU latencies (evict, then update Q and the
final valid K/V token):

| Batch / capacity | Valid lengths | Original / candidate / XQA (us) |
Paired latency reduction vs original |
| --- | --- | --- | ---: |
| 4 / 256 | 64, 127, 191, 256 | 31.344 / 13.392 / 36.352 | 57.22% |
| 1 / 1024 | 1024 | 44.808 / 21.608 / 49.152 | 51.87% |
| 1 / 4096 | 3968 | 112.264 / 93.728 / 111.952 | 16.58% |

These are GPU target measurements of the source-qualified schedules;
public package integration was validated separately below. Controlled KV
footprints do not establish cache hit rates, and the results do not
measure Python API or end-to-end model latency. Cold outliers were
retained. All cold/B4/short paired-median guards passed; a separate
cap64 confirmation retained one 6.54% regressing group, with only 0.63%
median regression for that condition.

Preparation checks tensor metadata; valid device sequence lengths remain
a caller precondition at every launch. The prepared interface requires
finite positive query scale and nonaliasing caller output, and
concurrent launches require independent prepared instances. The runnable
example demonstrates capture and dynamic lengths.

## 🔍 Related Issues

Follow-up to #5052. Experimental lifecycle: #5051 (owner @yyihuang).

## 🧪 Tests

- [x] Tests have been added as needed.
- [x] All focused tests passed on the intended hardware.

Validated the actual new public package on exact SM110 Thor, CUDA 13.4:

- **42/42 focused tests passed**, zero skipped: existing convenience API
plus 32 new prepared API cases.
- **84 FP32-oracle cases / 216 producer states** passed at FP16
atol=rtol=1e-2; **13 dynamic Graph states** passed through the public
entry points.
- The runnable Graph example passed.
- All six generated CUDA/binding files were checked against the
qualified source with only the declared symbol/comment renames; original
source files remain unchanged.
- **Synccheck passed** in 7.554 s with zero errors; **racecheck passed**
in 9.155 s with zero hazards/errors/warnings. Each had a separate hard
20-second process-group deadline.

The integration validation workflow took **83.582 s**.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

Ruff 0.12.8 `check` and `format --check` passed for all six changed
Python files. After the required explicit `zip(strict=True)` test
cleanup, all four affected stream tests passed again. `git diff --check`
passes.

- [ ] Full-repository `pre-commit run --all-files` (not run; focused
checks are reported above).

## 🔬 Experimental Track

- [x] This PR is experimental: new prepared APIs and backend
implementation. Tracking issue: #5051.
- [x] The tracking issue names an owner, reason and graduation plan.
- [x] Core changes are thin decorated entry points with deferred backend
handoff.
- [x] Focused tests were validated on the intended hardware; a runnable
example is included.
- [x] No AOT registration or automatic backend selection.
- [x] Test scope is declared below.

```experimental-tests
tests/experimental/test_sm110_gqa_decode.py
tests/experimental/test_sm110_gqa_decode_prepared.py
```

## Reviewer Notes

The existing original source closure and convenience implementation are
unchanged. New preparation/launch code lives in
`flashinfer/experimental/sm110_gqa_decode/prepared.py`; generated CUDA
and its manifest live in `csrc/prepared/`. The paired XQA driver/cubin
and full raw study receipts are not distributed in this PR; reproducing
the paired study requires that harness and baseline artifact.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added experimental prepared FP16 grouped-query-attention decode
support for SM110a hardware.
- Added public APIs to prepare and launch decode operations, including
configurable split execution.
- Added support for CUDA Graph capture and replay with updated sequence
lengths.
- Added an example demonstrating direct and graph-based prepared
decoding.

- **Documentation**
- Expanded experimental API documentation with prepared decode usage and
validation details.

- **Tests**
- Added coverage for accuracy, routing, CUDA Graph replay, stream
safety, and invalid inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [46188cf](https://github.com/flashinfer-ai/flashinfer/commit/46188cfc07bcec32a84d0b7462a958474d7953c7)

- **作者**: summer
- **时间**: 2026-09-17T21:08:43Z
- **提交信息**: [Bugfix] Consume CPU seq-len mirrors on the cute-dsl ragged prefill backend (#4816)

## 📌 Description

Follow-up to #4703 (per the discussion in
https://github.com/flashinfer-ai/flashinfer/pull/4703#discussion_r3877766942).
That PR taught `BatchPrefillWithRaggedKVCacheWrapper` to snapshot
`q_seq_lens_cpu` / `kv_seq_lens_cpu` at plan time and forward them at
run time, but only the `trtllm-gen` branch of
`trtllm_ragged_attention_deepseek` consumed them — `backend="cute-dsl"`
silently ignored the mirrors.

This matters because the CuTe DSL varlen kernel skips batches with
`seqlen_k <= 0` without writing their output rows, and `out` defaults to
`torch.empty`, so rows with `q_len > 0` and `kv_len == 0` return
uninitialized memory.

- Hoist the CPU-mirror validation out of the trtllm-gen branch so both
backends share it.
- On the cute-dsl branch, when mirrors are provided, neutralize empty-kv
rows before the launch (`out = 0`, `lse = -inf`), matching trtllm-gen's
empty-row semantics; skip the launch entirely when every row is empty.
Unlike trtllm-gen there is no in-kernel UB on empty rows, so no
compaction is needed — the kernel still sees the original uncompacted
tensors.
- The fill stays CUDA-graph-capturable: decisions read only the CPU
mirrors, and the fill itself uses only device-resident ops
(`repeat_interleave(..., output_size=...)` + `masked_fill_`).
- Mirrors remain optional on cute-dsl (no new raise for omitting them),
so existing all-active capture callers keep working.

Behavior note: previously the cute-dsl backend ignored the mirrors
entirely, including malformed ones; after this PR malformed mirrors
(unpaired, wrong device/dtype/shape, mismatched sums) raise a
`ValueError` on both backends. The wrapper always forwards a valid pair
snapshotted at plan time, so only direct callers passing invalid mirrors
are affected — and for them the raise replaces silent garbage.

Scope: the wrapper forwards mirrors only on its cute-dsl FMHA path
(`head_dim == 128`, no variant, no sliding window); the modular cute-dsl
path has no mirror contract and is unchanged here.

Perf: on the common all-active path the only addition is a few CPU-side
`.item()` reads on the CPU mirrors — no extra device work and no extra
launches.

Tests: mirror-validation tests, stubbed-kernel tests for the pre-launch
fill / skip-launch behavior, numerical parity against a compacted call,
and a wrapper-level CUDA-graph capture/replay integration test with
asymmetric zero-length rows (as suggested in #4703's review). The
real-kernel tests gate on SM100, which I don't have access to — verified
the wrapper logic on CPU with a stubbed kernel; would appreciate a CI
run for the kernel-level tests.

## 🔍 Related Issues

Follow-up to #4703 (and #4609 context).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Fixed ragged attention handling for rows with empty key/value
sequences in the Cute DSL backend.
* Empty rows now return defined neutral values instead of stale or
undefined results.
  * Improved handling of batches where all rows are empty.
  * Preserved CUDA graph capture and replay with zero-length rows.
  * Improved consistency between supported ragged-attention backends.

* **Tests**
* Added coverage for sequence-length validation, backend parity,
empty-row handling, and CUDA graph workflows.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: summer <128961079+zhang-keliang@users.noreply.github.com>
Signed-off-by: mingyangw <mingyangw@nvidia.com>
Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [a66fcc1](https://github.com/flashinfer-ai/flashinfer/commit/a66fcc126242468a1dafc47f97bebcb39691685b)

- **作者**: Misha Goin
- **时间**: 2026-09-17T20:57:48Z
- **提交信息**: fix(cli): use uv for kernel wheel installs in uv environments (#5299)

<!-- .github/pull_request_template.md -->

## 📌 Description

`flashinfer download-kernels` fails with `No module named pip` in
pip-free uv environments. Prefer `uv pip install --python <current
interpreter>` when `pyvenv.cfg` identifies a uv-created environment, or
when pip is unavailable and uv is on PATH.

Discovery uses a file read, `find_spec("pip")`, and `which("uv")`; it
does not import pip or launch installer probes.

## 🔍 Related Issues

None. Checked open uv/CLI installer PRs; no overlapping fix found.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] Changed-file hooks pass: `pre-commit run --files
flashinfer/__main__.py tests/cli/test_cli_cmds.py docs/cli.rst`.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] CLI suite: **46 passed**.

```bash
chg run -g=1 -- env FLASHINFER_WORKSPACE_BASE=/tmp/flashinfer-installer-cache \
  /home/mgoin/code/vllm/.venv/bin/python -m pytest tests/cli/test_cli_cmds.py -q
```

Also verified an offline local-wheel install into a temporary pip-free
uv environment with a conflicting `VIRTUAL_ENV`; only the explicitly
targeted environment was modified.

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

Scoped to wheel installation. The existing `pip download` step for
optional `--mode minimal` provider discovery still requires pip.

AI assistance was used for implementation and validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Wheel installation commands now automatically select the appropriate
installer.
* uv is preferred in uv-created environments or when pip is unavailable;
otherwise, the standard Python pip command is used.
  * Installations target the interpreter running FlashInfer.

* **Documentation**
  * Added CLI documentation explaining installer selection and behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: mgoin <mgoin64@gmail.com>

### [f16a9e5](https://github.com/flashinfer-ai/flashinfer/commit/f16a9e5425150a920520c823f0947f03d753f973)

- **作者**: Greg Fishman
- **时间**: 2026-09-17T20:57:26Z
- **提交信息**: fix(attention): size prefill partial outputs by query rows, not packed indices (#5177)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

The FA2 prefill planner reserves the split-KV buffers `tmp_v` and
`tmp_s` per (query row, head) pair instead of per query row.
With GQA that is group-size times too much: 16x for Qwen3.5 (32 query
heads, 2 KV heads).

Symptom: vLLM fails at startup on Qwen3.5-122B-A10B and
Qwen3.5-397B-A17B with `--max-num-seqs 512` or more:
`Buffer overflow when allocating memory for batch_prefill_tmp_v`.

What changes:

- The planner reserves per query row. The bound uses the same plan-time
values, so CUDA-graph replans keep their offsets.
- `plan()` checks that the planned rows fit.
- Decode with `use_tensor_cores=True` uses the same planner and benefits
too.
- Every CUDA-graph case now fits a workspace sized by
`workspace_size()`. The two prefill tests xfail'd for workspace overflow
are re-enabled and size their workspace that way.
- `tests/conftest.py` skips a CUDA OOM without keeping the test's GPU
tensors alive, and also catches an OOM re-raised by `assert_close`.
Before, one OOM skip left its tensors allocated and later tests failed
with OOM on small GPUs.

Workspace needed with CUDA graphs, head dim 256:

| case | query / KV heads | before | after |
| --- | --- | --- | --- |
| Qwen3.5: 512 sequences of 1 token | 32 / 2 | 514 MB | 32 MB |
| 128 sequences of 577 tokens | 32 / 4 | 18.4 GB | 2.3 GB |
| 128 sequences of 577 tokens | 32 / 1 | 72.7 GB | 2.3 GB |

Before, the Qwen3.5 case overflowed vLLM's 394 MB workspace with the
exact byte count from the reports. Now it fits.

End to end with vLLM main (435c96f9d) on an RTX 6000 Ada:
Qwen3.5-122B-A10B config with dummy weights, cut to 4 layers and 8
experts, `--attention-backend FLASHINFER --max-num-seqs 512`, default
CUDA graphs:

| FlashInfer | result |
| --- | --- |
| main | engine fails during CUDA graph capture: `Buffer overflow when
allocating memory for batch_prefill_tmp_v with size 536346624` |
| this PR | all PIECEWISE and FULL graphs captured (51 + 51), server
starts and returns a completion |

## 🔍 Related Issues

<!-- Link any related issues here -->

- vllm-project/vllm#40381 and vllm-project/vllm#40023: the startup crash
above, with the same byte count.
- Overlaps #4356, which sizes `tmp_v` by the output dtype. That PR
changes the bytes per row, this one the number of rows, so they compose.
Whichever lands second updates the same size expression and the size
check in `test_workspace_size.py`.
- Independent of #5176; they merge cleanly in either order.

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

Tests on main (e500442), CUDA 13.4 toolkit:

| test | GPU | before | after |
| --- | --- | --- | --- |
| `test_batch_prefill_kernels.py` | RTX 6000 Ada, 48 GB | 8788 passed,
5760 xfailed, 0 OOM skips, 0 failed | 13648 passed, 0 OOM skips, 0
failed |
| `test_batch_prefill_kernels.py` | RTX 4050 Laptop, 6 GB | 8709 passed,
5760 xfailed, 79 OOM skips, 0 failed | 13521 passed, 127 OOM skips, 0
failed |
| `test_batch_prefill_kernels.py` | RTX 3080, 10 GB, pure main as before
| 8694 passed, 5760 xfailed, 77 OOM skips, 17 failed (all OOM) | 13614
passed, 34 OOM skips, 0 failed |
| new: reservation per query row | RTX 4090 | 2 failed (8x
over-reserved) | 2 passed |
| new: exact-size workspace matches unsplit reference | RTX 4090 | 1
passed | 1 passed |

For the RTX 6000 Ada and RTX 4050 both columns use this PR's conftest;
the RTX 3080 compares pure main with this PR.
Comparing every test's outcome:

- RTX 6000 Ada: only the 5760 former xfails change (4860 pass, 900 hit
the test's own `qo_len > kv_len` skip).
- RTX 4050: the 5760 former xfails change (4800 pass, 900 hit the same
skip, 60 OOM skip), and 12 ragged custom-mask cases go from OOM skip to
pass.
- RTX 3080: the 5760 former xfails change (4860 pass, 900 hit the same
skip); of the upstream OOM outcomes, 10 failures and 50 OOM skips become
passes and 7 failures become OOM skips.

No test gets worse on any of the three GPUs.

`test_pod_kernels.py`: 168 passed, 24 skipped, 0 failed, before and
after (RTX 4090), and the same with this PR's conftest (RTX 6000 Ada).

Without the conftest change the RTX 4050 does fail. On the
`True-True-0.0` parametrizations: 24 OOM failures with the xfail kept,
59 with it removed, 0 in both cases with the change.

<details>
<summary>Performance and extra checks</summary>

No kernel changes. `run()` time changes by -0.6% to +0.6%, below
run-to-run noise; outputs are bitwise identical. Test file wall time:
3:50 before, 3:45 after.

`run()` on RTX 6000 Ada, all split-KV, median of 4 alternating rounds of
100 calls (round-to-round spread up to 3.5%):

| configuration | `run()` | change |
| --- | --- | --- |
| 512 sequences of 1 token, 32 / 2 heads, head dim 256, CUDA graphs |
2.51 ms | 0.0% |
| 16 sequences of 577 tokens, 32 / 4 heads, CUDA graphs | 2.10 ms |
+0.3% |
| 64 sequences of 127 tokens, 32 / 8 heads, CUDA graphs | 2.29 ms |
-0.6% |
| 16 sequences of 577 tokens, 32 / 4 heads, eager, `fixed_split_size=64`
| 2.85 ms | +0.6% |

- At the tests' old fixed 256 MB workspace, 1386 CUDA-graph cases
overflowed before and 414 after.
- 576 split-KV configurations vs the unsplit reference at 256 MB: 378
match and 198 do not fit before, 576 match after.
- 21,584 random plans (ragged lengths, sliding windows, fixed split
sizes): none exceeds the new bound.
- The last two checks ran on the previous base with CUDA 12.6.

</details>

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

- The row bound is `ceil_div(padded_batch_size * cta_tile_q,
gqa_group_size)`. It uses plan-time constants only, so CUDA-graph
replans keep the same offsets. `plan()` checks on the host that the
planned rows fit.
- FA3 has no `workspace_size`. In the two re-enabled tests it keeps the
fixed workspace; its planner has no split-KV partials.
- `tests/conftest.py`: only a `RuntimeError` raised while a CUDA OOM is
being handled becomes a skip. Assertion failures are untouched.

Generated with Claude Code and Human In The Loop 🙈


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Reduced temporary workspace allocation for split-KV prefill
operations, improving memory efficiency for grouped-query attention
workloads.
- Added runtime validation to detect insufficient workspace
reservations.
- Fixed CUDA Graph execution for paged key-value cache prefill by sizing
workspace correctly before capture.

- **Tests**
- Expanded coverage for workspace sizing, CUDA Graph execution, and
split-KV output correctness.
- Improved handling of CUDA out-of-memory conditions during test
execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: gf239 <gf239@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [2542f92](https://github.com/flashinfer-ai/flashinfer/commit/2542f922631052d3ac765780db3f5153961fc925)

- **作者**: Alex Yang
- **时间**: 2026-09-17T20:54:47Z
- **提交信息**: fix(tests): skip tests/prims_ts instead of erroring when CUTLASS DSL < 4.7 (#5215)

<!-- .github/pull_request_template.md -->

> **Rewritten.** This PR originally proposed raising the
`nvidia-cutlass-dsl`
> floor in `requirements.txt` to 4.7. That was wrong — see the comment
below;
> the low floor is deliberate. The branch name is a leftover from that
first
> attempt. The change here is entirely different.

## 📌 Description

`tests/prims_ts/conftest.py` calls `require_cutlass_dsl_experimental()`
at module
scope. Prims-TS imports `cutlass.experimental.primitives` and
`cutlass.experimental.task_scheduling`, which exist only in CUTLASS DSL
4.7+, so on
any environment resolved against our own declared floor
(`nvidia-cutlass-dsl>=4.6.2a0`)
that call raises during collection:

```
ERROR tests/prims_ts - RuntimeError: Prims-TS requires the CUTLASS DSL wheel.
Install the pinned release-branch wheel before using Prims-TS kernels.
```

It is a *collection* error, not a test failure, so it takes out the
entire
directory rather than the tests that actually need the wheel.

**Raising the floor is not the fix.** FlashInfer's lower bound is
aligned with
vLLM's and SGLang's on purpose: CuTe DSL is a diamond dependency, and
pinning up
would make FlashInfer unsatisfiable in those stacks. Features that need
4.7 are
meant to be gated at runtime and light up when the environment provides
them —
which is already the house pattern:

- `flashinfer/attention/cute_dsl/sm120_fmha.py` —
`_MIN_CUTLASS_DSL_VERSION = Version("4.7.0")`, checked at call time
- `flashinfer/kda.py` — needs `>=4.7`; below that `backend="auto"` falls
back to Cake, and only an explicit `backend='cute-dsl'` raises
- `flashinfer/attention/prims_ts/context.py` — guards a 4.8 feature the
same way

Prims-TS was the outlier. This makes it degrade like the rest.

The blanket require was also over-broad — **20 of the 21 test modules
here import
fine without the wheel**. Only
`test_batched_gemm_captured_schedule_tasks.py` pulls
in `batched_gemm_kernel` at module scope. Two of the modules it blocked,
`test_moe_bf16_support.py` and `test_moe_fp8_block_support.py`, call
`monkeypatch.setattr(support, "is_prims_ts_available", ...)` — they
exist precisely
to exercise the unavailable path, and could never run.

### Why mark collected items instead of skipping at module level

A module-level `pytest.skip(..., allow_module_level=True)` collects
**nothing**, so a
run scoped to this directory exits with pytest's "no tests collected"
code **5** —
trading one red for another. Marking collected items keeps them
collected, so the run
reports skips and exits **0**. I verified both behaviours directly
rather than
assuming:

| Mechanism | Report | Exit |
|---|---|---|
| `pytest.skip(allow_module_level=True)` in conftest | `1 skipped` |
**5** |
| `collect_ignore` only | `no tests ran` | **5** |
| `collect_ignore` + skip marker via `pytest_collection_modifyitems`
(this PR) | `3 skipped` | **0** |

As a side effect this makes `pytest_report_header`'s unavailable branch
reachable for
the first time — it could never fire before, because the require above
it raised first.
That dead branch is also the evidence that graceful degradation was the
original intent.

## 🔍 Related Issues

- Fixes #5213

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

This changes test collection behaviour, so the test *is* the CI run: on
a DSL 4.7
lane `tests/prims_ts` must run exactly as before (this path is a no-op
there), and on
a lane below 4.7 it must report skips instead of a collection error.

The collection mechanism itself was validated standalone —
`collect_ignore` drops the
un-importable module, every other module collects, all items report as
skipped, exit 0.

## Reviewer Notes

**Scope I deliberately did not take.** When the wheel is missing this
skips the whole
directory, including the ~8 modules that are pure Python and would pass
anyway
(`test_moe_api_signature.py`, `test_moe_config_packaging.py`,
`test_moe_tensor_adapter_validation.py`, the two `*_support.py` ones,
…). Narrowing the
skip to just the modules that reach the kernels would recover that
coverage, but it
means classifying each module by whether it touches `batched_gemm_*` at
runtime —
`test_moe_compile_cache.py` and `test_moe_nvfp4_support.py` do, and the
`test_batched_gemm_` filename prefix alone does not catch them. I kept
the behaviour
change minimal and symmetric (directory errors today → directory skips)
rather than
guessing at a classification I cannot verify without a 4.6.x box. Happy
to follow up
if you'd rather have the finer split.

**On coverage.** This does mean a lane below 4.7 reports green with
Prims-TS untested,
where today it reports red. That is the intended contract for a
version-gated feature,
but it only holds if at least one lane actually carries DSL ≥ 4.7 —
otherwise #4361
ships with no coverage anywhere and nothing says so. Worth confirming
that's true of
the Blackwell lanes. `scripts/setup_test_env.sh` already supports a
`CUTLASS_DSL_VERSION` override that does a clean uninstall first, which
looks like the
intended lever.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved Prims-TS test handling when the experimental runtime is
unavailable.
* Affected test modules are now ignored during collection instead of
causing collection failures.
* Collection errors now point to the appropriate test-collection
configuration for troubleshooting.

* **Tests**
* Added regression coverage confirming Prims-TS tests collect
successfully with limited experimental runtime support.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [7c19487](https://github.com/flashinfer-ai/flashinfer/commit/7c194873672f629f04bd3a862c3c881502419fed)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-17T16:49:46Z
- **提交信息**: fix(kda): force min_blocks_per_mp=1 on SM107 in WY output-only decode (#5253)

## 📌 Description

The KDA WY output-only decode kernel faults on SM107 (cc 10.7, Rubin)
once its grid needs more than
one wave: `Xid 13` → sticky `cudaErrorLaunchFailure`. This is the same
CuTe DSL defect as #4957 —
with `min_blocks_per_mp > 1` and no explicit `preferred_smem_carveout`,
the DSL auto-derives a
preferred SMEM carveout and applies it at module load — in the kernel
that was *derived from* the GDN
WY decode kernel #5227 fixes. That kernel and this one share their
PTX/layout helpers verbatim (see
the note at the top of `kda_decode_wy_output_only.py`), including the
launch-bound formula:

| | GDN WY decode (fixed in #5227) | KDA WY output-only decode (this PR)
|
|---|---|---|
| launch bound | `mbp = max(1, min(_needed + 1, 8))` | identical,
`:2328` and `:2552` |
| carveout | none | none (`:2385`, `:2625`) |
| grid | `(1, HV, B)` | `(1, HV, B)` (`:335`) |
| arch guard | `(10, 7) → mbp = 1` | **was missing — added here** |

Both entrypoints are reachable from the public KDA decode op with
`disable_state_update=True`;
`flashinfer/kda_decode.py` performs no compute-capability check.

### Why this had no coverage

Every pre-existing case in `tests/kda/test_kda_output_only.py` stays at
or below **204 CTAs**
(largest is `B=17, HV=12`), a single wave on any supported part. The
second trigger condition — grid
exceeds `num_sms × resident CTAs` — was therefore never met, which is
why no SM107 failure had been
reported for this kernel while #4957 was filed for the GDN one.

The first commit adds that missing case (grid sized off the device SM
count: `HV * B = 32` CTAs per
SM, several waves at any achievable occupancy), checked against the same
fp32 recurrent reference as
its neighbours. `T` does not enter the grid, so it stays at 1 to bound
the state pool.

### CI confirmation on Rubin, before the fix

Pipeline #68075462 ran the test-only commit. `unit_test_vr200_cu134`
reported **32 failures** in
`tests.kda.test_kda_output_only` with
`torch.AcceleratorError: CUDA error: unspecified launch failure`. That
number is the exact signature
of the sticky fault: the new case is collection item **19 of 50**, so it
is itself the first failure
and the **31** tests after it in the same process inherit the poisoned
context — 32 in total. The
**18** sub-wave cases collected ahead of it all passed. B200, GB300,
H100 and RTX Pro 6000 Blackwell
passed the same file on every CUDA column.

(The same job's 12 `tests.kda.test_recurrent_kda_cudnn_backend` failures
are a separate, host-side
`ValueError: backend='cute-dsl' does not support this recurrent_kda
prefill contract`, unrelated to
this kernel and not addressed here. The three `❔ Unknown` GB200 jobs
failed before producing a JUnit
report.)

### The fix

The same exact-match `(10, 7)` guard as #5227, at both `mbp`
computations. Site one reuses the `cc`
the function already queries for its cache key; site two hoists that
query above the `mbp`
computation so it can do the same, rather than adding a second device
query. `mbp` and `cc` are both
compile-cache-key components at both sites, so no stale module can be
reused. The
`FLASHINFER_KDA_OO_MBP` override is applied after the guard and still
wins, keeping the fault
reproducible on purpose.

No public API or behaviour change on any other architecture: the guard
is an exact capability match,
and `mbp` does not affect results (verified bit-identical below).

## 🧪 Tests

-
`tests/kda/test_kda_output_only.py::test_output_only_wy_grid_exceeds_one_wave`
— new; drives
`min_blocks_per_mp = 8` over 4736 CTAs on B200 (148 SMs) and passes in
1.5 s.
- `pytest tests/kda/test_kda_output_only.py` → **50 passed** on B200 /
CUDA 13.0, unchanged by the guard.
- With the compute capability faked to `(10, 7)` on B200:
`kda_wy_output_only` drops from `mbp=8` to
`mbp=1` with **bit-identical** output (`max|d| = 0.0`) at 4736 CTAs, and
`kda_recoverssm_verify`
drops from `mbp=2` to `mbp=1` with all 8 `test_recoverssm_dropin` cases
passing.
- `pre-commit run --files
flashinfer/kda_kernels/kda_decode_wy_output_only.py
tests/kda/test_kda_output_only.py`
  → clean.
- Rubin re-run requested below; the VR200 lane must go green on
`tests/kda/` for this to merge.

## 🔍 Related Issues

Same CuTe DSL defect as #4957; sibling fix to #5227.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved compatibility on SM107 GPUs by avoiding shared-memory
configuration faults in WY decode and RecoverSSM operations.
- Added coverage for WY output-only decoding across multi-wave CTA
workloads, helping validate results for larger launch configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [476f7bb](https://github.com/flashinfer-ai/flashinfer/commit/476f7bbddeef96148b5b30f5d78be3dc5e81d351)

- **作者**: Wookje Han
- **时间**: 2026-09-17T13:49:05Z
- **提交信息**: Enable PDL for intermediate quantization (#5281)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Propagate `enable_pdl` to the intermediate per-token NVFP4 quantization
launch between TRT-LLM MoE FC1 and FC2, using the existing checked
`launchWithPdlWhenEnabled` helper. Preserve the kernel's existing
dependency wait.

Add fixed-tactic PDL ON/OFF equivalence and fresh-input CUDA-graph
replay tests for M=1 and M=256 (H=4096, intermediate=2048, experts=32,
top-k=4).

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

- **Performance**
- Improved NVFP4 quantization execution for supported data types with
optional programmatic dependent-launch control.
- Extended per-token NVFP4 scaling support for mixture-of-experts
workloads.

- **Reliability**
- Improved consistency during CUDA Graph replays, including refreshed
inputs, updated outputs, and finite results.

- **Tests**
- Added coverage for NVFP4 MoE execution with and without
dependent-launch control across small and large token batches.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Wookje Han <wookjeh@nvl72d099-T17.cm.cluster>
Co-authored-by: Wookje Han <wookjeh@aws-cmh-slurm-1-login-02.cm.cluster>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4458
- **最后更新**: 2026-09-17T23:41:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34534
- **最后更新**: 2026-09-17T23:39:59Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: hf-security-analysis[bot], 陈志谦, Steven Liu

## AI分析总结

# diffusers 昨日提交分析（4 条）

## 1. 主要更新类型
- **文档更新为主**：4 条提交中 2 条为文档类（#14757、#14783），1 条为 CI 安全加固（#14798/#14800），1 条为工作流提醒逻辑调整（#14798）。
- 无新功能、无模型代码逻辑变更，属于典型的“维护型”提交批次。

## 2. 关键变更点与项目方向
- **#14757 文档批量修复**：将 8 处小修合并为一个 PR，覆盖 LTX latent 参数名、Kandinsky5 默认模板拼写（promt→prompt）、flux/hunyuan/kandinsky5 文档参数名与签名不一致、中文文档锚点、PAG 锚点、SD 概览死链、社区管线 TOC 死链等。体现项目对**文档准确性、中英双语一致性、死链治理**的持续投入。
- **#14783 重构 Get Started 章节**：优化入门文档结构，降低新用户上手门槛，符合 diffusers 作为扩散模型“一站式库”的定位。
- **#14798/#14800 CI 加固**：由安全分析机器人标记后修复 GitHub Actions 工作流，提升供应链安全。
- **#570b470**：调整 PR 关联 issue 提醒工作流，改善社区协作流程。

## 3. 对项目的影响与潜在意义
- 文档修复虽小，但**直接影响用户可复现性**：如 Kandinsky5 模板拼写修正会改变默认 token 序列，导致默认输出与上游参考仓库数值不一致——提交者已明确标注此权衡，体现严谨性。
- CI 加固降低被恶意 PR/工作流注入的风险，对高关注度开源仓库尤为重要。
- Get Started 重构有助于扩大用户基数，间接推动生态采用。

## 4. 值得关注的技术点
- **文档与代码签名一致性**是本次重点：多处 docstring 参数名与实际签名不符（如 flux 的 clip_skip、hunyuan 的 num_images vs num_videos），说明此前存在跨管线复制粘贴遗留问题。
- **中文文档锚点本地化**：英文锚点指向被翻译的中文标题会失效，需改用中文 slug，这是双语文档维护的常见坑。
- **默认模板拼写影响数值输出**：提示词工程中一个字母的差异会改变 token 序列，进而影响生成结果，值得使用者注意。

## 5. 结合项目背景的发展影响
diffusers 作为 HuggingFace 核心扩散模型库，用户群庞大且迭代快。此类“文档+CI”维护提交虽不改变模型能力，但**保障了库的可用性、安全性与可维护性**，是支撑其长期作为行业标准库的基础工作。文档准确性提升可减少用户误用与 issue 噪音，CI 加固则保护了项目供应链，整体上巩固了 diffusers 在扩散模型生态中的可信度与易用性优势。

## 详细提交记录

### [7221eef](https://github.com/huggingface/diffusers/commit/7221eef4573574925b67a69e9fc1482bf093e569)

- **作者**: 陈志谦
- **时间**: 2026-09-17T16:48:07Z
- **提交信息**: docs: pool eight small doc fixes into one PR (#14757)

* docs: fix latent -> latents in LTX latent upsampler docstrings

__call__ takes 'latents' (the docstring said 'latent', and its own
description says 'Input latents to normalize').

* docs: fix 'promt' typo in kandinsky5 default prompt templates

The default system template sent to the Qwen text encoder misspelled
'prompt engineer' as 'promt engineer' (4 pipelines).

Note: this changes the token sequence of the default template, so
default outputs will differ numerically from before / from the
upstream Kandinsky5 reference. If exact parity with the reference
repo is preferred, the reference itself would need the same fix.

* docs: fix docstring parameter names that do not match signatures

- flux controlnet encode_prompt documented a clip_skip parameter that
  does not exist (copy-paste from SD-style docs; flux has no CLIP
  layer-skipping)
- hunyuan_video1_5 pipelines documented num_images_per_prompt while
  the parameter is num_videos_per_prompt
- kandinsky5 _encode_prompt_qwen/_encode_prompt_clip documented
  num_videos_per_prompt, which neither method accepts

* docs(zh): fix English anchors pointing at translated Chinese headings

speed-memory-optims.md linked ./memory#model-offloading and
#group-offloading while the zh memory page translates those headings
(模型卸载 / 组卸载); using_peft_for_inference.md linked #hotswapping
while the zh heading is 热切换. Repointed at the Chinese slugs.

* docs: fix PAG anchor and the StableDiffusionPipelineSafe row in the SD overview

- pag.md linked #pagappliedlayers; the heading '### pag_applied_layers'
  keeps its underscores (#pag_applied_layers)
- the SD overview table linked ./stable_diffusion_safe, a doc page that
  no longer exists anywhere under docs/source; the row now names the
  deprecated pipeline as plain text instead of a dead link

* docs: fix dead Masked Im2Im TOC anchors in community pipelines README

The TOC rows linked #stable-diffusion-masked-im2im /
#stable-diffusion-xl-masked-im2im; the actual headings are
'Masked Im2Im Stable Diffusion Pipeline' and 'Masked Im2Im Stable
Diffusion Pipeline XL' (lines 3184/3219).

* docs(examples): drop duplicated 'with' in T5/Gemma sequence-length help strings

16 example scripts' --max_sequence_length help read 'to use with with
the T5 text encoder' (or the Gemma variant); surfaced in --help output.

* fix(links): keep the pag_applied_layers anchor in doc-builder form

doc-builder slugifies headings by dropping underscores, so the heading
'### pag_applied_layers' anchors as #pagappliedlayers — the form the
check-links CI expects. GitHub-style underscores broke it.

Signed-off-by: simpleqt <89645338+simpleqt@users.noreply.github.com>

* fix(kandinsky5): recompute prompt_template_encode_start_idx after the promt fix

Correcting 'promt' -> 'prompt' in the system templates shifts each
template's token count by one (verified with the Qwen2.5-VL tokenizer:
41->40, 55->54, 129->128, 129->128). Without this, the hardcoded start
indices slice the encoded prompt one token off.

---------

Signed-off-by: simpleqt <89645338+simpleqt@users.noreply.github.com>

### [37ce5ad](https://github.com/huggingface/diffusers/commit/37ce5add81f5b0838b744f03dcc2238ffc740cbc)

- **作者**: Steven Liu
- **时间**: 2026-09-17T15:06:40Z
- **提交信息**: [docs] Refactor get started section (#14783)

* docs

* feedback

* feedback

### [654dac8](https://github.com/huggingface/diffusers/commit/654dac8880acda22dd7b9fa0531afaaedd1335fa)

- **作者**: hf-security-analysis[bot]
- **时间**: 2026-09-17T12:01:00Z
- **提交信息**: fix(ci): harden GitHub Actions workflows (#14798) (#14800)

fix(ci): harden workflow files flagged on #14798

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

### [570b470](https://github.com/huggingface/diffusers/commit/570b470947bd83987d57c1b2d3e4a5d8ded8763b)

- **作者**: Sayak Paul
- **时间**: 2026-09-17T11:57:16Z
- **提交信息**: changes in the pr_link_issue_reminder workjflow (#14798)

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
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


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13130
- **最后更新**: 2026-09-17T13:01:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36110
- **最后更新**: 2026-09-18T00:16:12Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 24
- **主要提交者**: silencejade, chuyeh, Lianmin Zheng

## AI分析总结

# SGLang 昨日提交分析总结

## 1. 主要更新类型

本批 28 个提交以**功能新增**和**Bug修复**为主，辅以**性能优化**、**重构**、**CI/文档**调整。覆盖面广，横跨 AMD ROCm、NPU（昇腾）、Router、HiCache、Diffusion、多模态等多个子系统，体现了 SGLang 作为高性能 LLM 推理服务框架的多硬件、多场景并行演进特征。

## 2. 关键变更点及与项目方向的关系

- **PD 运行时角色切换（#28403）**：允许 prefill 与 decode 节点在运行时动态切换角色，这是对 PD 分离架构的重要增强，提升集群弹性与资源利用率。
- **DSV4 系列（#39921、#35123、#37778）**：将注意力元数据、稀疏 prefill、KV pool 泛化到压缩比维度，并修复 AMD FP4 反量化路径、启用 hicache，说明项目正深度适配 DeepSeek-V4 等新模型。
- **Router 增强（#39170、#39133、#38983）**：引入 min-load 随机候选采样、chat 渲染对齐、dynamo-render 支持，强化路由层的负载均衡与渲染一致性。
- **HiCache 优化（#39050、#29668）**：批量 D2H 提交与 Mooncake 节点级 hostname 解析，持续打磨分层缓存性能与部署可靠性。
- **Radix Cache 演进（#34012）**：引入 Agentic-Aware 尾部优化 LRU 淘汰策略，面向 Agent 场景优化缓存命中。
- **NPU 生态扩展（#39427、#39438、#39413、#38420）**：上下文并行、MXFP8/W4A4F8 量化、NCCL 权重加载、SwigluLimit 激活等，系统性补齐昇腾支持。

## 3. 对项目的影响与潜在意义

这些变更共同强化了 SGLang 的**多硬件后端统一性**（AMD/NPU/CUDA）与**生产级弹性**（PD 角色切换、路由负载均衡）。DSV4 与 Agentic 缓存优化表明项目紧跟前沿模型与 Agent 应用趋势。安全方面（#39858 限制 SafeUnpickler）提升了反序列化安全性，对生产部署意义重大。

## 4. 值得关注的技术点

- **运行时 PD 角色切换**：可能改变集群调度范式，需关注一致性保证。
- **压缩比泛化的注意力/KV pool**：为稀疏与压缩模型提供统一抽象。
- **Agentic-Aware LRU**：将缓存淘汰策略与 Agent 工作负载特征结合，是较新颖的方向。
- **SafeUnpickler 全局限制**：安全加固的典型实践。

## 5. 基于项目背景的发展影响

SGLang 定位为高性能 LLM 推理框架，本批提交延续其**“多硬件 + 多模型 + 生产可用”**主线：一方面通过 NPU/AMD 适配扩大硬件覆盖，另一方面通过 PD 切换、路由优化、HiCache 提升大规模部署的弹性与效率。整体看，项目正从“单机高性能”向“集群级弹性推理服务”演进，同时兼顾安全与前沿模型支持，方向清晰且执行密集。

## 详细提交记录

### [7bc9152](https://github.com/sgl-project/sglang/commit/7bc915244742263e831db4e1f725e54edbb3ed5d)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-17T23:37:48Z
- **提交信息**: [Test] Consolidate kernel tests under plural kernels tree (#39966)

### [b98a2d1](https://github.com/sgl-project/sglang/commit/b98a2d1096f6dac51ea2e77376f398d1d4cfd551)

- **作者**: Khoa Pham
- **时间**: 2026-09-17T23:17:25Z
- **提交信息**: [Docs] GLM-5.3-Flash cookbook: temporarily remove the DCP option (#40036)

### [1f0c73e](https://github.com/sgl-project/sglang/commit/1f0c73e9bd3d2b7c5f72b86304d1936b2ff6adc1)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-17T22:55:19Z
- **提交信息**: [DSV4] Generalize attention metadata, sparse prefill, and KV pool over compress ratios (#39921)

### [4f52a27](https://github.com/sgl-project/sglang/commit/4f52a2756328df5c27c9c6b76011805f7f40e8f8)

- **作者**: Ren Yuzhou
- **时间**: 2026-09-17T20:51:22Z
- **提交信息**: [AMD] Fix DSV4 FP4 dequant path for AITER on ROCm (#35123)

Co-authored-by: Ren Yuzhou <yuzhouo7@users.noreply.github.com>

### [126c2f1](https://github.com/sgl-project/sglang/commit/126c2f1bc13fc072aa1345a13ac79a62e8d8bfde)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-17T20:39:00Z
- **提交信息**: [CI] Add metamergebot to CI permissions (#40017)

### [72d9419](https://github.com/sgl-project/sglang/commit/72d9419bef89177b9cae7af6e3d751d9825cc471)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-17T19:09:09Z
- **提交信息**: [Router] Sample k random candidates for the min-load fallback (--min-load-choices) (#39170)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [6c73368](https://github.com/sgl-project/sglang/commit/6c73368c329f811472829927d7185f189e3c8ff3)

- **作者**: Thomas Wang
- **时间**: 2026-09-17T18:29:23Z
- **提交信息**: [AMD][DSV4] Enable hicache on deepseek-v4 fp8 unified attn (#37778)

### [1f60dde](https://github.com/sgl-project/sglang/commit/1f60ddef5dc2ae3bbfbe0c5cea45690c4b60a251)

- **作者**: inkcherry
- **时间**: 2026-09-17T17:45:12Z
- **提交信息**: [PD] Introduce runtime role switching between prefill and decode (#28403)

Signed-off-by: huanglong <huanglong@linux.alibaba.com>
Signed-off-by: inkcherry <mingzhi.liu@amd.com>
Co-authored-by: huanglong <huanglong@linux.alibaba.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Huang Long <121648372+LLLL114@users.noreply.github.com>

### [a98d921](https://github.com/sgl-project/sglang/commit/a98d921658b2cb78ca1257a4d72a6a3969620456)

- **作者**: Byron Hsu
- **时间**: 2026-09-17T16:21:09Z
- **提交信息**: [DP Attn] Fix crash for no token all-gather case (#39899)

Co-authored-by: Byron Hsu <byron+per@periodiclabs.ai>

### [25c9f72](https://github.com/sgl-project/sglang/commit/25c9f724d4785eaa6921690d1634d20a3faac57b)

- **作者**: Zhuangcheng(Jesse) Gu
- **时间**: 2026-09-17T16:20:21Z
- **提交信息**: fix(multimodal): handle tensor images in exact-token preprocessing (#30368)

Signed-off-by: Zhuangcheng(Jesse) Gu <zcgu@connect.hku.hk>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [e4cbb28](https://github.com/sgl-project/sglang/commit/e4cbb28ea1ad6289b04e438950c57f2eba810c09)

- **作者**: Kan Wu
- **时间**: 2026-09-17T15:53:40Z
- **提交信息**: [router] Improve SGLang chat render parity (#39133)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [7ccbf5f](https://github.com/sgl-project/sglang/commit/7ccbf5fd04f7ee23095fc38e49e749d58dc18282)

- **作者**: pllimax
- **时间**: 2026-09-17T12:50:33Z
- **提交信息**: [NPU][CI] Increase e2e multi-node test timeout to 210 minutes (#39952)

### [a9fb1c3](https://github.com/sgl-project/sglang/commit/a9fb1c32384695bde87877c9e5e468a272356380)

- **作者**: vstone-w
- **时间**: 2026-09-17T11:59:41Z
- **提交信息**: dsv4(npu): support prefill context parallelism with interleave and zigzag (#39427)

### [11c35b8](https://github.com/sgl-project/sglang/commit/11c35b8433e887d4ad02d1dc8f084dd1937de08c)

- **作者**: jacky.cheng
- **时间**: 2026-09-17T11:56:31Z
- **提交信息**: [AMD] Load fused shared experts for Qwen4-Exp and Qwen3.5 MTP (#38878)

### [a1b4ec0](https://github.com/sgl-project/sglang/commit/a1b4ec02ae07b8beaced5cb229d960f04d773562)

- **作者**: Arseniy Mironov
- **时间**: 2026-09-17T10:13:05Z
- **提交信息**: [NPU][Diffusion] FA MXFP8 and modelslim w4a4f8 and w8a8f8 support for Wan2.2 and FLUX (#39438)

### [6ca866e](https://github.com/sgl-project/sglang/commit/6ca866ea29271242b567b0f438bffe5b53a81c4a)

- **作者**: Shuwen Wang
- **时间**: 2026-09-17T09:53:58Z
- **提交信息**: [HiCache][Perf] fix: batch HiCache D2H submits per step for hybrid pools (#39050)

### [1a90ae6](https://github.com/sgl-project/sglang/commit/1a90ae6727014089e4e90ab81773429e3df08032)

- **作者**: yl3469
- **时间**: 2026-09-17T09:52:59Z
- **提交信息**: Add Agentic-Aware Tail-Optimized LRU eviction to the unified radix cache (#34012)

Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [575759d](https://github.com/sgl-project/sglang/commit/575759d90af942eeff89f1c8c33a1fcdb2da4181)

- **作者**: silencejade
- **时间**: 2026-09-17T09:28:15Z
- **提交信息**: [NPU] Support nccl backend for --remote-instance-weight-loader (#39413)

### [e970453](https://github.com/sgl-project/sglang/commit/e970453b433e1467e22f6d925f270563417540b5)

- **作者**: AndyLi429
- **时间**: 2026-09-17T08:40:32Z
- **提交信息**: [NPU]Refactor weight processing and add NPUSwigluLimit activation (#38420)

Co-authored-by: AndyLi429 <AndyLi429@noreply.gitcode.com>
Co-authored-by: Even Zhou <even.y.zhou@outlook.com>

### [2d08cc5](https://github.com/sgl-project/sglang/commit/2d08cc5ede61b86e34462067414bfcf39fd6d859)

- **作者**: chuyeh
- **时间**: 2026-09-17T08:29:14Z
- **提交信息**: [AMD][Spec] Enable GDN ReplaySSM target-verify on ROCm (#38184)

Co-authored-by: chuyeh <298092489+chuyeh@users.noreply.github.com>

### [acfde25](https://github.com/sgl-project/sglang/commit/acfde25d345d45960003b4428a0b6f9bb412d14e)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-17T08:17:15Z
- **提交信息**: Carry deferred attention operands and reuse multimodal shared memory (#39870)

Co-authored-by: fei-xx <135589532+fei-xx@users.noreply.github.com>
Co-authored-by: jmswen <jmswen@gmail.com>

### [8825774](https://github.com/sgl-project/sglang/commit/882577451e764a515df2a386a055012e8f075a16)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-17T08:09:55Z
- **提交信息**: Restrict SafeUnpickler standard-library globals (#39858)

Co-authored-by: jiayisuse <jiayisuse@fb.com>

### [71ef869](https://github.com/sgl-project/sglang/commit/71ef869eceb0c14a75681339f7aeb3d10890838a)

- **作者**: chuyeh
- **时间**: 2026-09-17T08:06:04Z
- **提交信息**: [AMD][Bugfix] Fix vattn_asm HIP error 709 under CUDA graph capture on ROCm 10 (#39513)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [3ce7e2a](https://github.com/sgl-project/sglang/commit/3ce7e2a29f01195fc4feceef00f62feadc37bfd9)

- **作者**: Kan Wu
- **时间**: 2026-09-17T07:57:20Z
- **提交信息**: [sgl-router] Render chat prompts with dynamo-render (#38983)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [15b256b](https://github.com/sgl-project/sglang/commit/15b256bdb04be6cfdbc56c359af27ffd5abc18fe)

- **作者**: Teng Ma
- **时间**: 2026-09-17T07:51:21Z
- **提交信息**: [HiCache] fix: resolve Mooncake local_hostname per node for runtime attach (#29668)

Co-authored-by: Teng Ma <11641725+stmatengss@users.noreply.github.com>

### [aebae58](https://github.com/sgl-project/sglang/commit/aebae58b8c7894287a9ea8b5d844c65bbb58c9b2)

- **作者**: Shijin Zhang
- **时间**: 2026-09-17T07:25:17Z
- **提交信息**: [Moe] Fix flashinfer_trtllm silently dropping swiglu_limit clamped SwiGLU activation (#39920)

### [f3c0256](https://github.com/sgl-project/sglang/commit/f3c02567712d4f195e8e0ed1eae8d5c830936543)

- **作者**: Mick
- **时间**: 2026-09-17T07:16:35Z
- **提交信息**: [diffusion] chore: remove retired auto-residency workload helpers (#39884)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [44bd359](https://github.com/sgl-project/sglang/commit/44bd35908230c4f363c83dbe34fe25749d985950)

- **作者**: faceless void
- **时间**: 2026-09-17T07:08:20Z
- **提交信息**: [NPU][Diffusion] Optimize SenseNova-U1 batched generation (#39382)

Signed-off-by: syd520zy <529477025@qq.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1282
- **最后更新**: 2026-09-17T21:50:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92033
- **最后更新**: 2026-09-18T00:06:13Z

## 提交统计

- **昨日提交总数**: 66
- **提交者数量**: 56
- **主要提交者**: Shantipriya Parida, Shuolei Wang, coderfornow

## AI分析总结

# vLLM 昨日提交综合分析

## 一、主要更新类型

昨日共 66 个提交，以 **Bug 修复** 为绝对主力（约 30+ 条），覆盖 ROCm、XPU、MoE、KV Cache、前端与编译等模块；**性能优化** 同样密集，包括 DFlash2 融合分组卷积、AITER QuickReduce+RMSNorm 融合、EPD 图像批处理、MiniMax-M3 稀疏 PA 免拷贝插入、DeepGEMM warmup 复用 MoE workspace 等；**功能新增** 方面有 `release_kv_cache_memory()` API、Cohere2MoE Eagle3 支持、POWER W8A8 INT8 MoE、多模态 V2 对 encoder-only ViT 的 CUDA Graph 捕获；此外还有大量 CI/构建调整（ROCm/The Rock、NVIDIA Rubin CUDA 13.4、多模态 Processor 分片）以及文档、类型与重构类改动。

## 二、关键变更与项目方向

- **多硬件后端持续扩展**：ROCm（AITER、The Rock、MI355）、XPU、POWER、s390x、NVIDIA Rubin 均有提交，跨平台战略清晰。
- **KV Cache 管理精细化**：新增释放 API、修复 stale workspace、offload 分块注册、跳过 scratch 组。
- **MoE 与稀疏注意力深化**：TRT-LLM 权重布局封装、SP 填充行跳过、FlashInfer BF16 就地转换、DeepGEMM Mega-Gate 集成。
- **新模型适配**：Qwen DFlash、GLM-5.3-Flash、Kimi K3、DSv4.1、Cohere2MoE 等，紧跟前沿发布节奏。
- **多模态与内核调优**：ViT 图捕获、FlashInfer 自动调优隔离、ROCm 分阶段 H2D 拷贝、DeepSeek V4 WKV 投影堆叠、Qwen4Exp QSA sm_90 调优表。

## 三、对项目的影响与意义

大量 ROCm/AMD 修复表明 AMD 生态正被认真对待，有助于打破 NVIDIA 单一依赖；`release_kv_cache_memory()` 等前端 API 增强提升服务端资源可控性，利于生产部署；多处崩溃修复（GLM-5.3-Flash boot crash、ROCm MoE 崩溃回退）直接提升稳定性与用户信任；多模态 CUDA Graph 捕获可显著降低 ViT 前向调度开销，对高并发多模态服务吞吐有直接收益。CI 分片、超时调整与测试退役则反映项目规模膨胀带来的工程治理压力。

## 四、值得关注的技术点

DFlash2 融合分组卷积可能显著降低特定模型延迟；DeepGEMM Mega-Gate 集成进一步释放 DeepSeek 系性能；AITER QuickReduce+RMSNorm 融合属 ROCm 高阶优化；DP index 用于 dense DP 权重更新修正了分布式正确性；xgrammar 控制字符转义关乎结构化输出安全；encoder-only ViT 图捕获如何与 V2 调度器协同、FlashInfer 调优隔离的作用域管理、ROCm 分阶段 H2D 拷贝的带宽与延迟权衡，均值得跟进。

## 五、结合 README 的发展判断

README 定位为“Easy, fast, and cheap LLM serving for everyone”。本日提交中，**fast** 由多项融合与 MoE 优化支撑，**cheap** 由 KV Cache 释放、内存过分配修复与量化支持体现，**everyone** 则由 ROCm/XPU/POWER/s390x 多平台覆盖兑现。整体看，vLLM 正从“支持多模型”走向“多硬件、多场景、生产级稳定”的成熟阶段，高密度 Bug 修复也说明用户基数与部署规模在快速扩大。

## 详细提交记录

### [48f663c](https://github.com/vllm-project/vllm/commit/48f663c37f8c77803d9281778d49ec0727abcacf)

- **作者**: Yan Ma
- **时间**: 2026-09-17T23:52:01Z
- **提交信息**: [XPU] Fix incorrect context-key normalization for Qwen DFlash-based models (#56431)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [092bdd6](https://github.com/vllm-project/vllm/commit/092bdd6d57ac7c1cd5272339c80372053fd51bbe)

- **作者**: Dakai An
- **时间**: 2026-09-17T23:12:12Z
- **提交信息**: [Frontend][Core] Add release_kv_cache_memory() API (#44890)

Signed-off-by: Dakai An <dakaian108@gmail.com>
Signed-off-by: AlanFokCo <alanfok2868@gmail.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Dakai An <77474977+andakai@users.noreply.github.com>
Co-authored-by: AlanFokCo <alanfok2868@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [a524f80](https://github.com/vllm-project/vllm/commit/a524f80b1f0dd85889bf227310670ee8fdcd5fd2)

- **作者**: Oxana Korzh
- **时间**: 2026-09-17T23:09:06Z
- **提交信息**: [AMD][Bugfix] Make the nested-RoPE patch reach automatic validation (#57289)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [ccde9c6](https://github.com/vllm-project/vllm/commit/ccde9c61e958d9dbfc21af6c62df6ff15881c811)

- **作者**: Wei Zhao
- **时间**: 2026-09-17T23:01:35Z
- **提交信息**: [Bugfix] Restore KV cache metadata GET method for external event consumer (#56925)

Signed-off-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [e0050f2](https://github.com/vllm-project/vllm/commit/e0050f287aae8b3ddbe2947a5af1c5dd23db2781)

- **作者**: Mustafa YILDIRIM
- **时间**: 2026-09-17T22:34:56Z
- **提交信息**: [Bugfix][ROCm] Add record_logical_topk_ready to ROCMAiterMLASparseImpl (GLM-5.3-Flash boot crash) (#57252)

Signed-off-by: Mustafa YILDIRIM <mustafa@character.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [80447d2](https://github.com/vllm-project/vllm/commit/80447d27655918da6bfbccd0d3a40e975bda220a)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-17T22:14:37Z
- **提交信息**: [Bugfix][DSv4.1] Fix FlashInfer DSpark non-causal attention (#57432)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [d3074ac](https://github.com/vllm-project/vllm/commit/d3074acddade913b530e192143b3611f58938ce3)

- **作者**: rasmith
- **时间**: 2026-09-17T22:13:13Z
- **提交信息**: [AMD][CI][The Rock] Fix language models standard for The Rock on mi355 (#53837)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [e8a2a0a](https://github.com/vllm-project/vllm/commit/e8a2a0a8bbe675885ced6efddd49c1da0ff0a218)

- **作者**: Shimi Bandiel
- **时间**: 2026-09-17T22:02:00Z
- **提交信息**: [Bugfix][Frontend] Reject stop strings on --tokens-only servers instead of silently ignoring them (#57058)

Signed-off-by: Shimi Bandiel <shimib@google.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ac78445](https://github.com/vllm-project/vllm/commit/ac78445bc9ee3bb615b8b21db22fb7dac6698ece)

- **作者**: Misha Goin
- **时间**: 2026-09-17T21:47:30Z
- **提交信息**: [MoE] Encapsulate TRT-LLM BF16 weight layout handling (#57405)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [db7a24c](https://github.com/vllm-project/vllm/commit/db7a24c230a4db6ae3a568ed01b01f3f7172069d)

- **作者**: Misha Goin
- **时间**: 2026-09-17T21:38:59Z
- **提交信息**: [Perf] Add fused DFlash2 grouped convolution (#55960)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [668d6c3](https://github.com/vllm-project/vllm/commit/668d6c3a778b9ac525f78d39b0c413c8604235d1)

- **作者**: Thang Nguyen
- **时间**: 2026-09-17T21:11:40Z
- **提交信息**: [CI] Shard multimodal Processor 1->4 (#56316)

Signed-off-by: Thang Nguyen <thang.nguyen@inferact.ai>
Co-authored-by: Thang Nguyen <thang.nguyen@inferact.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Kimi Code <noreply@moonshot.ai>

### [9612f77](https://github.com/vllm-project/vllm/commit/9612f77077e09acbae9cc1d1b2ddf14a23e91597)

- **作者**: Maroon Ayoub
- **时间**: 2026-09-17T20:23:15Z
- **提交信息**: [Bugfix] Release stale FlashMLA workspace views after growth (#56902)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [acc2ed2](https://github.com/vllm-project/vllm/commit/acc2ed2a5f1fbe79575a220fc743a80c2d068ce8)

- **作者**: rasmith
- **时间**: 2026-09-17T20:20:35Z
- **提交信息**: [ROCm][CI][The Rock 10] Fix (MI355) Quantized Models failure on The Rock 10 with Triton 3.8.x (#54849)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [2b02c6c](https://github.com/vllm-project/vllm/commit/2b02c6c29b72147de18905ba4e7dc8f284655b40)

- **作者**: Doug Brown
- **时间**: 2026-09-17T20:09:36Z
- **提交信息**: [Model] Add Cohere2MoE Eagle3 auxiliary hidden states (#49819)

Signed-off-by: Doug Brown <doug@github.douggo.com>

### [9a5bd37](https://github.com/vllm-project/vllm/commit/9a5bd373cfe59e236f2b32c30530f4dbbf24120d)

- **作者**: Misha Goin
- **时间**: 2026-09-17T20:04:03Z
- **提交信息**: [CI] Retire Weight Loading smoke tests (#57398)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [ac2f0ea](https://github.com/vllm-project/vllm/commit/ac2f0ea82c0d3005eb1de081cda715f0ee524c16)

- **作者**: Elvir Crnčević
- **时间**: 2026-09-17T19:36:19Z
- **提交信息**: [MoE][Bugfix] Skip SP padded rows in grouped MoE routing (#56079)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [67e5b0a](https://github.com/vllm-project/vllm/commit/67e5b0acc9988afc50d019db64ad9da0dadaa15e)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-17T19:26:10Z
- **提交信息**: [Bugfix][HiSparse][NIXL] Import full blocks without tail prefill on D (#57049)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>

### [41f9104](https://github.com/vllm-project/vllm/commit/41f9104fa649aed2c26af8a459210619ad9514fe)

- **作者**: Thien Tran
- **时间**: 2026-09-17T19:06:36Z
- **提交信息**: [DSv4.1] Integrate Mega-Gate from DeepGEMM (#56266)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [a9a7e45](https://github.com/vllm-project/vllm/commit/a9a7e45f3174781f2b20c03c7ac1beee2b98f9d5)

- **作者**: afriedri
- **时间**: 2026-09-17T18:39:52Z
- **提交信息**: [ROCm] Restore `VLLM_ROCM_USE_AITER_FP4_ASM_GEMM` and default w4a4 ASM GEMM back to off (#57055)

Signed-off-by: Andy Friedrich <afriedri@amd.com>

### [6a344d8](https://github.com/vllm-project/vllm/commit/6a344d8c8595fc7ca32a633b6f146d36dd227430)

- **作者**: Michele Campi
- **时间**: 2026-09-17T18:19:13Z
- **提交信息**: [Bugfix][Metrics] Do not log a 0.0% prefix cache hit rate before any query (#54990)

Signed-off-by: Michele Campi <215741962+MicheleCampi@users.noreply.github.com>

### [09c379a](https://github.com/vllm-project/vllm/commit/09c379ab6183085fd90e8195792cc63f5247cdf3)

- **作者**: Andy Lo
- **时间**: 2026-09-17T18:09:18Z
- **提交信息**: [Bugfix] Max-load throughput cliff when `max_num_seqs` is not a multiple of 8 (#57355)

Signed-off-by: Andy Lo <andy@mistral.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [ff6b580](https://github.com/vllm-project/vllm/commit/ff6b5808c4571a37ba3d27f74d74ef43c3a14245)

- **作者**: Sriram Kumar
- **时间**: 2026-09-17T17:51:35Z
- **提交信息**: [ROCm] Resolve the indexer fp8 cache dtype once at import (#53792)

Signed-off-by: Sriram Kumar <sriramkumar.kishorekumar@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [f3aa88d](https://github.com/vllm-project/vllm/commit/f3aa88d2309523f8438a239a55f59a28179ce5ef)

- **作者**: Wentao Ye
- **时间**: 2026-09-17T17:05:52Z
- **提交信息**: [Kimi K3 Bug] Fix kimi k3 reasoning parser (#57098)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [b2f2bd7](https://github.com/vllm-project/vllm/commit/b2f2bd71ba6cff6d0678e2f83d45c1c08425144c)

- **作者**: vllm-agent
- **时间**: 2026-09-17T17:02:24Z
- **提交信息**: [CI][Bugfix] Add tp_shard_with_padding to padded MoE reload test mock (#57402)

Signed-off-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Co-authored-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [e30bf70](https://github.com/vllm-project/vllm/commit/e30bf70c5dfb90fd9b31a8f4692b49df9b223704)

- **作者**: Matt
- **时间**: 2026-09-17T16:22:39Z
- **提交信息**: [ROCm][CI] Fix Entrypoints Integration (Pooling) tests on TheRock image (#57380)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [fef55fd](https://github.com/vllm-project/vllm/commit/fef55fd26dc633fcc87978f12f1a97e08e351c02)

- **作者**: Matt
- **时间**: 2026-09-17T16:21:22Z
- **提交信息**: [ROCm][CI] Adapt MoE tests to the triton_kernels 3.8 API (#57385)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [e960ead](https://github.com/vllm-project/vllm/commit/e960ead0aa70362a57f205be831083b68c7a5bdb)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-17T16:11:31Z
- **提交信息**: [Mypy] Fix mypy typing for Transformers models (#54320)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [b78fbab](https://github.com/vllm-project/vllm/commit/b78fbab4be552650286778a9e489980d850f76c3)

- **作者**: Young
- **时间**: 2026-09-17T15:52:10Z
- **提交信息**: [Docs] Fix the typos in the document (#57190)

Co-authored-by: Young <yangchh15@163.com>

### [d7e755c](https://github.com/vllm-project/vllm/commit/d7e755c23080988f7450f107466d6f6a74b042ff)

- **作者**: Ziyang Ma
- **时间**: 2026-09-17T15:50:14Z
- **提交信息**: [Bugfix] Fix wrong vLLM version reported by pip install (proto-v* tag collision) (#57295)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Codex <noreply@openai.com>

### [6a7de3b](https://github.com/vllm-project/vllm/commit/6a7de3ba3ad95965e41618568ff803fa01ab168d)

- **作者**: Zoe923
- **时间**: 2026-09-17T15:49:56Z
- **提交信息**: [Bugfix][GDN] Fix CuteDSL BF16 KKT inversion divergence (#53864)

Signed-off-by: Zoe923 <871844693@qq.com>

### [493d4b3](https://github.com/vllm-project/vllm/commit/493d4b3c04a439c926df2c4d2fa3cdfabb1a8605)

- **作者**: HieDean
- **时间**: 2026-09-17T15:20:37Z
- **提交信息**: [bugfix] Mark draft tokens to rebuilt their embeddings. (#57356)

Signed-off-by: HieDean <799287043@qq.com>
Co-authored-by: hiedean <hiedean@tju.edu.cn>

### [1df336c](https://github.com/vllm-project/vllm/commit/1df336c3bab8e2ac2eb3d325bd90e62b94656e9c)

- **作者**: Mikko Tukiainen
- **时间**: 2026-09-17T15:05:48Z
- **提交信息**: [Perf][ROCm] Enable AITER QuickReduce + RMSNorm fusion (#48249)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4f9a41a](https://github.com/vllm-project/vllm/commit/4f9a41ac94beb940249d9712a6dd2996cf37da61)

- **作者**: Tyler Michael Smith
- **时间**: 2026-09-17T15:05:31Z
- **提交信息**: [CI/Build][Hardware][NVIDIA] Add Rubin CUDA 13.4 nightly images (#55953)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3affd35](https://github.com/vllm-project/vllm/commit/3affd35f3164ba17503ba63cd8733becd1b03bf1)

- **作者**: vllmellm
- **时间**: 2026-09-17T14:52:12Z
- **提交信息**: [Fix][ROCm] MXFP4 MoE round-up inflates TP-sharded expert weights on CDNA3, starving KV cache (#56359)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [438434b](https://github.com/vllm-project/vllm/commit/438434b5b5f8936a4dc7d651c708928c90f085d6)

- **作者**: akii96
- **时间**: 2026-09-17T14:44:54Z
- **提交信息**: [ROCm][Perf] Insert MiniMax-M3 sparse-PA K/V without a contiguous copy (#56849)

Signed-off-by: Aakif Nawaz <aakif.nawaz@amd.com>

### [9e1cd26](https://github.com/vllm-project/vllm/commit/9e1cd262cbf43b3f3839a28cfa151e2e4b27e2d8)

- **作者**: Alexander Lee
- **时间**: 2026-09-17T14:44:36Z
- **提交信息**: [Bugfix] Use DP index for dense DP weight updates and EC CPU region (#56950)

Signed-off-by: lxy-alexander <lxy_alexander@outlook.com>
Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [861a299](https://github.com/vllm-project/vllm/commit/861a299adc72bbbb1b60853b6173075465a6b425)

- **作者**: Robert Shaw
- **时间**: 2026-09-17T14:11:14Z
- **提交信息**: [Bugfix][Model Runner V2] Route dummy tokens to MoE experts during profiling (#57270)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [78fdf4e](https://github.com/vllm-project/vllm/commit/78fdf4efb86dffde1b0f5733207aed038c3530f8)

- **作者**: Yuchen Wang
- **时间**: 2026-09-17T14:00:04Z
- **提交信息**: [Bugfix][MoE] Convert FlashInfer BF16 weights in place (#54699)

Signed-off-by: Yuchen Wang <93700456+yuchenwang3@users.noreply.github.com>
Signed-off-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [117cf43](https://github.com/vllm-project/vllm/commit/117cf43fb65713a0a7a3c35b23be078d5fb319d4)

- **作者**: Rukhaiya2004
- **时间**: 2026-09-17T13:45:13Z
- **提交信息**:  [HARDWARE][POWER] Enable W8A8 INT8 MoE on POWER (#55316)

Signed-off-by: Rukhaiya <bibirukhaiya123@gmail.com>
Signed-off-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: Antigravity <antigravity@google.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [0eae9ac](https://github.com/vllm-project/vllm/commit/0eae9acd4d01574e12d4ecf6a0229813f7fdb799)

- **作者**: Shantipriya Parida
- **时间**: 2026-09-17T13:39:26Z
- **提交信息**: [Bugfix][ROCm][MoE] Fall back instead of crashing when AITER MoE is requested for a non-gated (is_act_and_mul=False) model (#56590)

Signed-off-by: Shantipriya Parida <shantipriya.parida@amd.com>

### [fe284ea](https://github.com/vllm-project/vllm/commit/fe284ea17d606ceba4a5d3d55d3e3d9a34f478d9)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-17T13:35:34Z
- **提交信息**: [BugFxi] Fix DeepGEMM FP8 workspace over allocation (#53914)

Signed-off-by: Lucas Wilkinson <lwilkinson@neuralmagic.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [75c7139](https://github.com/vllm-project/vllm/commit/75c71390d5b399f5397a9166920fc45902f99f14)

- **作者**: CaiJohn
- **时间**: 2026-09-17T12:57:47Z
- **提交信息**: [Bugfix] Escape control characters in xgrammar choice grammar (#48115)

Signed-off-by: john <6712432+CaiJohn@users.noreply.github.com>
Co-authored-by: john <6712432+CaiJohn@users.noreply.github.com>

### [0ef8366](https://github.com/vllm-project/vllm/commit/0ef8366ba39fc38b88c60b17ee2ddf05aa8a7596)

- **作者**: Harry Mellor
- **时间**: 2026-09-17T12:53:11Z
- **提交信息**: [Frontend] Only show the summary line of config docstrings in `--help` (#57357)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [8be3ca3](https://github.com/vllm-project/vllm/commit/8be3ca35f311fc205262122aedcf775d56ebc3ac)

- **作者**: Matt
- **时间**: 2026-09-17T12:52:02Z
- **提交信息**: [ROCm][CI] Fix AMD CI pipeline upload rejected by an invalid block-step key (#57375)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [f46968c](https://github.com/vllm-project/vllm/commit/f46968cb6e28ff89182bfa6fc291b4f851ab07d1)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-17T12:42:59Z
- **提交信息**: [CI] Make ci-clean-log.sh portable to macOS/BSD sed (#57367)

Signed-off-by: khluu <khluu000@gmail.com>

### [2e50824](https://github.com/vllm-project/vllm/commit/2e50824766ead3e30f53cba711e8c7ffb2bb6b2b)

- **作者**: Martín el Cheikh
- **时间**: 2026-09-17T12:27:54Z
- **提交信息**: [Bugfix] Fall back to native sampling when FlashInfer cannot target the GPU (#48956)

Signed-off-by: martin el cheikh <martinelcheikh@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a85dd55](https://github.com/vllm-project/vllm/commit/a85dd55177d59b99903432c71c7376309d7e7757)

- **作者**: Laura Lopez-Real
- **时间**: 2026-09-17T12:22:57Z
- **提交信息**: Fix Laguna patch mutating flat RoPE parameters (#57189)

Signed-off-by: Laura López Real <laulopezreal@users.noreply.github.com>
Co-authored-by: Laura López Real <laulopezreal@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [91a4c40](https://github.com/vllm-project/vllm/commit/91a4c40b45696c4dd31281877ad46af0910efcfa)

- **作者**: Wentao Ye
- **时间**: 2026-09-17T12:04:56Z
- **提交信息**: [Compile] Fix compile warning #177-D (#56609)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [667b26e](https://github.com/vllm-project/vllm/commit/667b26e50bc3287793efd92672c520fa101ecf80)

- **作者**: Simon Danielsson
- **时间**: 2026-09-17T12:02:39Z
- **提交信息**: [Bugfix][ROCm][GLM-5.3-Flash] Apply deferred tilelang.jit already on attribute access (#57192)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>

### [da3c07b](https://github.com/vllm-project/vllm/commit/da3c07bf7dda0c5cbe94d06854426907cd30c7ed)

- **作者**: Yan Ma
- **时间**: 2026-09-17T11:57:22Z
- **提交信息**: [XPU][CI] skip test_hybrid_prefix_cache_hit_rate (#57301)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [9ff08f9](https://github.com/vllm-project/vllm/commit/9ff08f9493aa745b0559c02cf6148f71d9817169)

- **作者**: aoshen02
- **时间**: 2026-09-17T10:46:28Z
- **提交信息**: [Bugfix] Honor skip_reading_prefix_cache for KV connector hits (#57269)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>

### [0d72627](https://github.com/vllm-project/vllm/commit/0d726275653800e82c324e1d32b074f782e89315)

- **作者**: Tianyu Guo
- **时间**: 2026-09-17T10:45:52Z
- **提交信息**: [Perf][EPD] Batch image requests per encoder (#57095)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>
Signed-off-by: Zhou ziheng <jiaranran2@gmail.com>
Co-authored-by: Zhou ziheng <jiaranran2@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [99ea5f5](https://github.com/vllm-project/vllm/commit/99ea5f525da6b5428f2c5740f3cd15377f284c1d)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-17T10:34:00Z
- **提交信息**: [CI] Raise DSv4-Flash disaggregated engine readiness timeout to 1800s (#57334)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Kimi <noreply@moonshot.cn>

### [683f6c8](https://github.com/vllm-project/vllm/commit/683f6c8edf9656da99926bbe5aae5ffffaa850b3)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-17T10:33:44Z
- **提交信息**: [CI] Raise H200 LM Eval Large Models timeout to 120 min (#57335)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Kimi <noreply@moonshot.cn>

### [b6e7c1f](https://github.com/vllm-project/vllm/commit/b6e7c1f1f0430b5d4784aea391c42067581b7f76)

- **作者**: Itay Etelis
- **时间**: 2026-09-17T10:22:49Z
- **提交信息**: [kv_offload] Skip scratch groups (#57145)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [40b40d1](https://github.com/vllm-project/vllm/commit/40b40d1d39bb82563dd699be3456abaa95d0722a)

- **作者**: drakosha
- **时间**: 2026-09-17T10:19:56Z
- **提交信息**: [Bugfix][KV Offload] Register the offload region in chunks (#51081)

Signed-off-by: Mikhail Kostryukov <mike@triptrack.net>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Colton Ottley <coltonottley@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [08633cb](https://github.com/vllm-project/vllm/commit/08633cb5cd77ea315351ae531945a9a253016788)

- **作者**: Canlin Guo
- **时间**: 2026-09-17T08:56:28Z
- **提交信息**: [Qwen3.8-Flash-Next] Enable FP8 TP with FlashInfer TRTLLM MoE (#55867)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [f1c2f6a](https://github.com/vllm-project/vllm/commit/f1c2f6ada80f7c0d896b7870f53db97103ff339d)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-17T08:44:11Z
- **提交信息**: [ROCm][CI] Stage H gating and MI355 test reallocation (#57080)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [23cd034](https://github.com/vllm-project/vllm/commit/23cd0346cec1cb98862d93e0c1bfa490f827e6a3)

- **作者**: Tianmu Li
- **时间**: 2026-09-17T08:43:08Z
- **提交信息**: [CPU] Align scheduler and NIXL CPU affinity per local rank (#53636)

Signed-off-by: Li, Tianmu <tianmu.li@intel.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [88afb77](https://github.com/vllm-project/vllm/commit/88afb777008bab6d33a6f5ea965e2a0d83a0a7ec)

- **作者**: coderfornow
- **时间**: 2026-09-17T08:35:17Z
- **提交信息**: [CPU][s390x] Pin protobuf to 7.36.1 and drop C++ extension removal workaround (#54978)

Signed-off-by: coderfornow <Ritik.Dhiranan@ibm.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [de24e51](https://github.com/vllm-project/vllm/commit/de24e5190820cc6640f2d55295405f228fffbc41)

- **作者**: jiangkuaixue123
- **时间**: 2026-09-17T08:12:17Z
- **提交信息**: [MM][V2] Enable encoder-only ViT CUDA graph capture (#56922)

Signed-off-by: jiangkuaixue123 <jiangxiaozhou111@163.com>
Co-authored-by: Codex <noreply@openai.com>

### [4e5ffda](https://github.com/vllm-project/vllm/commit/4e5ffda19d897f3c34455167dc0503620f1b3e2a)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-09-17T07:38:58Z
- **提交信息**: [Bugfix] Isolate supplemental FlashInfer BF16 autotuning (#57285)

Signed-off-by: jiahanc <173873397+jiahanc@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [528fa83](https://github.com/vllm-project/vllm/commit/528fa835fd37d0805a824d516e22f88df61a771a)

- **作者**: JohnQinAMD
- **时间**: 2026-09-17T07:14:43Z
- **提交信息**: [ROCm] Stage large pageable H2D copies instead of registering them (#56343)

Signed-off-by: JohnQinAMD <yanyuan.qin@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [b3079e6](https://github.com/vllm-project/vllm/commit/b3079e6e46a21109a8641c6d48641453a9c7cb86)

- **作者**: leo
- **时间**: 2026-09-17T07:04:53Z
- **提交信息**: [Perf][DSpark] Stack DeepSeek V4 context WKV projections (#54674)

Signed-off-by: liuyao0322 <yaoliu548926@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [7bbce75](https://github.com/vllm-project/vllm/commit/7bbce752b85f183eb34e27ea6df9647f80986060)

- **作者**: Shuolei Wang
- **时间**: 2026-09-17T07:02:24Z
- **提交信息**: [Perf][Model] Qwen4Exp QSA: sm_90 tuning table for _select_config (#57273)

Signed-off-by: Shuolei Wang <shuoleiwang123@gmail.com>
Signed-off-by: Shuolei Wang <948904026@qq.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [bd2d7ae](https://github.com/vllm-project/vllm/commit/bd2d7ae7c197ba995800bb03a23b4d79c38627a4)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-17T07:01:19Z
- **提交信息**: [Perf] Reuse MoE workspace for DeepGEMM warmup (#57268)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-18
**监控日期**: 2026-09-17
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6858
- **最后更新**: 2026-09-18T00:09:34Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 17
- **主要提交者**: Nick Cao, Tiago de Souza Fernandes, amy-why-3459

## AI分析总结

# vllm-omni 昨日提交批次分析（19 条）

## 1. 主要更新类型
- **Bug 修复**（约 6 条）：MoE+Diffusion 并行状态初始化、MAGI-2 分层卸载 OOM、MiniCPM-o 双工切片与静音续接、Voxtral 参考音频校验、CI 配置测试。
- **功能新增**（约 4 条）：π0.5 VLA 模型、MiniCPM-o/Qwen3-Omni 共享实时 Web UI、FastH3 8-Step V2 检查点加载、MOSS-TTS 参考音频编码器 GPU 放置。
- **性能优化**（约 4 条）：ERNIE-Image 与 LongCat 的 Q/K RoPE 融合、Qwen3-Omni DeepStack 冗余文本嵌入移除、PersonaPlex RingKV 行偏移。
- **重构/清理**：移除部署配置中的 `shm_threshold_bytes`、统一 worker 侧 MP4 编码、Realtime 编解码器抽离复用。
- **文档**：NPU 平台 MiniMax-H3 Ascend 配方刷新。

## 2. 关键变更点与项目方向
- **多模态覆盖持续扩张**：新增 π0.5（VLA 机器人动作模型）与 FastH3 图像模型，呼应 README "omni-modality serving" 定位，从文本/语音/图像向具身智能延伸。
- **实时交互能力强化**：Realtime 编解码器复用化（RFC #6592 P0a）、共享 Web UI、MiniCPM-o 双工修复，表明项目正把"实时全双工"作为核心差异化方向。
- **XPU/NPU 多硬件后端**：Intel XPU 修复 HunyuanImage-3、Ascend 文档刷新，体现"for everyone"的跨平台承诺。
- **性能内核融合**：连续两条 RoPE 融合提交，说明团队在扩散/生成模型推理效率上持续投入。

## 3. 影响与潜在意义
- 并行状态初始化与 OOM 修复直接提升 MoE+Diffusion 混合负载的稳定性，是生产可用性的关键。
- Realtime 编解码器"可复用化"为后续统一实时 API 奠定架构基础，属长期收益型重构。
- π0.5 的引入可能打开 VLA/机器人赛道，扩展项目受众边界。

## 4. 值得关注的技术点
- **RoPE 融合**（ERNIE-Image、LongCat）在 eager 执行下减少算子开销，是低延迟推理的典型手段。
- **RingKV 行偏移与 active rows**：面向长上下文/多行并行的细粒度控制，值得跟踪其扩展性。
- **参考音频编码器 GPU 放置**：TTS 流水线阶段间设备编排的优化思路。
- **MP4 编码统一**：多模型视频输出路径收敛，降低维护成本。

## 5. 结合项目背景的发展影响
README 强调"易用、快速、低成本的全模态服务"，本批次提交在三个维度推进该目标：**广度**（新增 VLA、图像、TTS 模型）、**稳定性**（多项 OOM/初始化修复）、**效率**（内核融合与冗余消除）。同时多硬件后端与实时交互的持续投入，显示项目正从"支持多模态"走向"生产级实时全模态服务"，架构上通过编解码器复用和编码路径统一为后续规模化扩展铺路。

## 详细提交记录

### [6bda549](https://github.com/vllm-project/vllm-omni/commit/6bda549ac23a667efbe44a54cf3f6d57e6e24da2)

- **作者**: Alex Brooks
- **时间**: 2026-09-17T23:15:37Z
- **提交信息**: [Bugfix] Fix Parallel State Initialization For MoE + Diffusion (#7676)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [77d8de7](https://github.com/vllm-project/vllm-omni/commit/77d8de70da6851a504d435df8bc8a0d6ff4913e3)

- **作者**: Joshna-Medisetty
- **时间**: 2026-09-17T19:23:27Z
- **提交信息**: [XPU][HunyuanImage3] Fix HunyuanImage-3.0 text-to-image on XPU (#7674)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>

### [b81f2c5](https://github.com/vllm-project/vllm-omni/commit/b81f2c5d4be41d35664bd7b7ccea74396348ed8b)

- **作者**: Nick Cao
- **时间**: 2026-09-17T19:22:14Z
- **提交信息**: [Misc] treewide: remove shm_threshold_bytes from deploy config (#7522)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [a6570b6](https://github.com/vllm-project/vllm-omni/commit/a6570b68140cded3aa00e1fa6cddd78a869db6fe)

- **作者**: dongbo910220
- **时间**: 2026-09-17T19:06:45Z
- **提交信息**: [Diffusion] Fuse ERNIE-Image Q/K RoPE for eager execution (#7502)

Signed-off-by: dongbo910220 <1275604947@qq.com>

### [9cdc57d](https://github.com/vllm-project/vllm-omni/commit/9cdc57d2e7297d0621dcc5c02cf392ee9857e1ec)

- **作者**: BeatSeat
- **时间**: 2026-09-17T19:02:08Z
- **提交信息**: [Bugfix][MAGI-2] Fix layerwise offload OOM by pointing offload block attrs to 'block' (#7523) (#7540)

Signed-off-by: BeatSeat <wendavid552@gmail.com>

### [97912de](https://github.com/vllm-project/vllm-omni/commit/97912de8d8b9b2ad8877cea5d356c4551686ab7f)

- **作者**: dongbo910220
- **时间**: 2026-09-17T18:27:57Z
- **提交信息**: [Kernel] Fuse LongCat paired Q/K RoPE (#7500)

Signed-off-by: dongbo910220 <1275604947@qq.com>

### [2ab5d17](https://github.com/vllm-project/vllm-omni/commit/2ab5d1701a98502ab1f0ebe48c90b45d31eeb8fe)

- **作者**: Anjie Hou
- **时间**: 2026-09-17T15:33:56Z
- **提交信息**: [4/N] Unify worker-side MP4 encoding and wire Wan into it (#7048)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [882bf8b](https://github.com/vllm-project/vllm-omni/commit/882bf8bc95b1a9a08af667a7edd006ebd21e4b57)

- **作者**: amy-why-3459
- **时间**: 2026-09-17T15:32:31Z
- **提交信息**: [Frontend] Add a shared realtime web UI for MiniCPM-o and Qwen3-Omni (#7222) (#7585)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [eb1abba](https://github.com/vllm-project/vllm-omni/commit/eb1abbadf832c625a9560cb6e0142d2cec4998ce)

- **作者**: Canlin Guo
- **时间**: 2026-09-17T12:51:26Z
- **提交信息**: [Feature][TTS] MOSS-TTS: place the reference-audio encoder on the code2wav stage's GPU (#7724)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>

### [c61b302](https://github.com/vllm-project/vllm-omni/commit/c61b30255bc2099a947ccf7bf0955f73c139d277)

- **作者**: howard.shan
- **时间**: 2026-09-17T12:47:10Z
- **提交信息**: [Qwen3-Omni] Remove redundant text embedding in DeepStack path (#7573)

Signed-off-by: howard-shan <shanwenhao668@gmail.com>
Signed-off-by: howard.shan <shanwenhao668@gmail.com>

### [5b22f55](https://github.com/vllm-project/vllm-omni/commit/5b22f5562f630ba571cc70d99f104ff01ba87f49)

- **作者**: Tiago de Souza Fernandes
- **时间**: 2026-09-17T12:26:34Z
- **提交信息**: fix(minicpmo45): deadline-align native duplex silence continuation (#7059)

Signed-off-by: Tiagosf00 <tiagotsf2000@gmail.com>

### [d0755b5](https://github.com/vllm-project/vllm-omni/commit/d0755b57169352c07416ad925385bdc907781e8c)

- **作者**: Chenchao Xu
- **时间**: 2026-09-17T12:18:51Z
- **提交信息**: [Model] Add π0.5 (Pi0.5) VLA model support (#6950)

Signed-off-by: chenchaox <chenchaox@nvidia.com>

### [873e9bf](https://github.com/vllm-project/vllm-omni/commit/873e9bff7c545c5cda79fdb93a867f09e443b61d)

- **作者**: ooooooye
- **时间**: 2026-09-17T11:05:15Z
- **提交信息**: [Doc][NPU] Refresh MiniMax-H3 Ascend recipes for 0.28-era configurations (#7720)

Signed-off-by: brandneway <gyuan4892@gmail.com>

### [bf74544](https://github.com/vllm-project/vllm-omni/commit/bf74544a35bb45d6092fb2b568e01fc51859b09b)

- **作者**: Clodagh Walsh
- **时间**: 2026-09-17T10:56:58Z
- **提交信息**: [Voxtral] Follow up to raise BadRequest for ref_audio (#7649)

Signed-off-by: Clodagh Walsh <clodaghwalsh17@gmail.com>

### [f5e4f5f](https://github.com/vllm-project/vllm-omni/commit/f5e4f5fa429ae3b5a8c50e83785900faea1ecc7b)

- **作者**: Tianyao Wu
- **时间**: 2026-09-17T10:35:46Z
- **提交信息**: [Bugfix][MiniCPM-o] Size the duplex HD slice reservation from the frame (#7654)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e3be42e](https://github.com/vllm-project/vllm-omni/commit/e3be42e052e88d052d21cf7a24ee84c70f020fd6)

- **作者**: psv666
- **时间**: 2026-09-17T09:33:40Z
- **提交信息**: [Core] Give the OpenAI Realtime wire codec a reusable home (RFC #6592 P0a) (#7640)

Signed-off-by: psv666 <2693925048@qq.com>

### [825ab20](https://github.com/vllm-project/vllm-omni/commit/825ab20b07268050015516f9a65c733d7d089d28)

- **作者**: MrDongsls
- **时间**: 2026-09-17T08:50:40Z
- **提交信息**: [Model][PersonaPlex] add per-row RingKV offsets and active rows (#7670)

Signed-off-by: Mr.Dong <1042542469@qq.com>
Co-authored-by: Mr.Dong <1042542469@qq.com>

### [cb439f3](https://github.com/vllm-project/vllm-omni/commit/cb439f3e84394c0cdfc252eaff3303fb099cc67d)

- **作者**: WeiQing Chen
- **时间**: 2026-09-17T08:41:52Z
- **提交信息**: [Diffusion][Model] Add direct FastH3 8-Step V2 checkpoint loading (#7610)

Signed-off-by: david6666666 <530634352@qq.com>

### [8c3d340](https://github.com/vllm-project/vllm-omni/commit/8c3d3407d1bc9b1b538d2196f4ed2d802a15cfc3)

- **作者**: Alex Brooks
- **时间**: 2026-09-17T07:01:01Z
- **提交信息**: [CI] Fix Structured Structured Diffusion Config Wan Test (#7707)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

---
