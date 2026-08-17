---
title: "iqView: Putting the Model Inside the Viewer"
date: 2026-07-12T09:10:00+02:00
draft: false
categories: ["Research & Development"]
tags: ["Computer Vision", "Generative AI", "Segmentation", "C++", "Qt", "Photography Workflow"]
featured_image: "featured.png"
description: "A fork of qView with LaMa inpainting, FLUX.2 generation and SAM 3 segmentation running locally on your own GPU — plus XMP-compatible culling, so nothing is locked inside the app."
---

### The Question

Most AI image tooling assumes you will come to it. You open a separate
application, import, wait, operate, export. That round trip is small in absolute
terms and enormous in practice, because it converts a two-second impulse — *that
lamp post ruins the shot* — into a task.

**iqView** asks the opposite question: what if the model lived where you were
already looking? It is a fork of [qView](https://github.com/jurplel/qView), a
genuinely minimal image viewer, with three models wired directly into the browsing
surface.

![iqView with a retouch mask active](featured.png)

### Three Models, Three Keystrokes

- **`R` — Object removal.** *LaMa* inpainting. Mask a distraction with a brush or
  lasso and it is gone in a fraction of a second.
- **`G` — Creative fill.** *FLUX.2 klein*. Mask a region, type a prompt, get
  photo-real replacement content in seconds.
- **`S` — Isolate.** *SAM 3*. One-click subject cutout to a transparent PNG.

Everything runs **locally**, on your own CUDA GPU — developed on an RTX 3090. Your
photographs never leave the machine. That is not a marketing line; it is the
reason the tool is usable on client material at all.

There is no configuration step. iqView bootstraps its own portable Python
environment via [uv](https://github.com/astral-sh/uv) the first time you actually
press one of those keys. Opening and browsing images works immediately, with no
Hugging Face account and no setup, because the AI environment is only touched on
first genuine use. An optional idle prefetch warms LaMa a few seconds after you
settle on an image, so `R` never has a cold start.

### The Part Nobody Expects: Culling

The feature I use most is not generative at all. Rate images as you browse — `1`
to `5` for stars, `X` to reject, `0` to clear — and the ratings are written to
**XMP sidecar files** using the same `xmp:Rating` convention that Lightroom,
Bridge, digiKam and Photo Mechanic read.

That means you can cull here and finish elsewhere. **Edit → Rate → Export
Keepers…** copies everything at or above a star threshold into a folder, sidecars
included.

I care about this disproportionately. A tool that traps your decisions inside its
own database has taken something from you in exchange for convenience. Writing to
an interchange format that four competing applications already agree on costs
almost nothing and gives the work somewhere to go afterwards.

### Honest Platform Status

The C++ viewer builds with **Qt 6 / CMake** and passes CI on Windows, Linux and
macOS. The Python AI pipeline has only ever actually been *run* on Windows with an
NVIDIA GPU.

| Platform | Viewer | AI features |
|---|---|---|
| Windows + NVIDIA | ✅ | ✅ Verified — primary development environment |
| Windows, no NVIDIA | ✅ | ⚠️ CPU fallback works, slowly |
| macOS | ✅ builds via CI | ❓ Untested on hardware — torch ships MPS support |
| Linux + NVIDIA | ✅ builds via CI | ❓ CUDA path exists, never run on real Linux hardware |

**I am looking for testers on macOS and Linux.** Even confirming that the viewer
itself opens and browses smoothly is useful — an issue on the repository is the
place for it. **Help → Export Debug Report…** writes a single text file with
platform details and AI log tails, deliberately excluding your Hugging Face token
and any image data.

### Model Licences

The models are downloaded on demand, never bundled: **LaMa** (Apache 2.0),
**FLUX.2-klein** (Apache 2.0, cleared for commercial use), and **SAM 3** (Meta's
SAM licence — gated, requiring your own Hugging Face token and acceptance of
Meta's terms).

[View source on GitHub &rarr;](https://github.com/cyberhirsch/iqView)

*Based on the original [qView](https://github.com/jurplel/qView) by Jurplel.*
