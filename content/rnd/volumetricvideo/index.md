---
title: "Temporal Gaussian Hierarchy: Reproducing a SIGGRAPH Paper, and Beating It"
date: 2026-07-12T09:50:00+02:00
draft: true
categories: ["Research & Development"]
tags: ["Volumetric Video", "Gaussian Splatting", "Research Reproduction", "CUDA", "Neural Rendering"]
description: "A from-scratch reproduction of Xu et al.'s Temporal Gaussian Hierarchy (SIGGRAPH Asia 2024) on a single RTX 3090 — reaching 32.08 dB PSNR against the paper's reported 29.44."
---

### The Project

Volumetric video means recording a real scene from many cameras at once and
replaying it in 3D, from any viewpoint, in VR. The technique works beautifully for
a few seconds and then falls over: Gaussian-Splatting approaches store per-frame
state, so cost grows with duration and a minute-long capture becomes intractable.

**"Representing Long Volumetric Video with Temporal Gaussian Hierarchy"** (Xu et
al., SIGGRAPH Asia 2024, [arXiv:2412.09608](https://arxiv.org/abs/2412.09608))
proposes a fix. I reproduced it from scratch — no reference implementation — as a
plugin on top of [EasyVolcap](https://github.com/zju3dv/EasyVolcap), trained on a
single consumer GPU.

I do this kind of reproduction deliberately, and I recommend it to students for
the same reason: reading a paper produces the *feeling* of understanding, and
reimplementing it produces the thing itself. Every ambiguity the authors glossed
over becomes a decision you are forced to make.

### The Result

Neural3DV `flame_salmon` — the paper's own canonical benchmark. 50,000
iterations, RTX 3090, random initialisation (no SfM init):

| Metric | This reproduction | Paper (TGH) | 4DGS | 3DGS+T |
|---|---|---|---|---|
| **PSNR** | **32.08 dB** | 29.44 dB | 28.89 dB | 28.61 dB |
| **SSIM** | **0.970** | 0.945 | 0.952 | 0.950 |
| **LPIPS** | **0.197** | 0.214 | 0.197 | 0.210 |

The image quality is not merely reproduced, it is exceeded — by 2.6 dB on the
paper's own numbers.

I want to be precise about what that does and does not mean. It is an
**image-quality** result. The paper's *system* headline figures — VRAM ceiling,
frames per second, on-disk footprint — depend on engineering pieces I left out of
scope, and I make no claim about those. A reproduction that overstates its own
reach is worth less than one that draws the line.

### What Was Actually Built

All three of the paper's contributions, implemented, self-tested, and validated
end-to-end:

- **`GaussianModel4D`** — the 4D Gaussian primitive: dual-quaternion 4D rotation,
  conditional-3D extraction, Compact Appearance hook, 4D adaptive density control.
- **`TemporalGaussianHierarchy`** — hierarchy placement (Eq. 6), query (Eq. 7),
  and re-assignment.
- **`GaussianTHSampler`** — the integration plugin registered into EasyVolcap.

Seven files in total, plus one patched upstream file (a pycolmap API-drift fix)
and three configs. The modules carry runnable self-tests: `python -m
easyvolcap.utils.gaussian4d_utils` exercises the 4D primitive maths directly.

### Live Viewer

A WebSocket render server loads a trained checkpoint and streams frames to a
browser client — orbit with the mouse, scrub the time slider through the
sequence. Beyond the colour image, the viewer can display each 4D Gaussian's
**implicit velocity** (`Σ_xt / Σ_tt`) colour-coded with the Middlebury
optical-flow wheel, which turns the learned motion field into something you can
actually look at rather than infer.

### Constraints

Trained under WSL2 on one **RTX 3090 (24 GB)**, entirely in userspace, no sudo.
At the full 1200-frame setting the 24 GB is genuinely at its ceiling — longer
sequences need more memory, and that limit is a real finding rather than an
inconvenience.

[View source on GitHub &rarr;](https://github.com/cyberhirsch/VolumetricVideo)

*Source and documented methodology only — the trained checkpoints and datasets
are far too large for version control.*
