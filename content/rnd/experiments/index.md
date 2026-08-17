---
title: "Experiments: A Laboratory Notebook in Public"
date: 2026-07-12T09:15:00+02:00
draft: false
categories: ["Research & Development"]
tags: ["Generative Art", "Physics", "WebGL", "WebGPU", "Computational Aesthetics"]
featured_image: "featured.png"
launch_url: "https://cyberhirsch.github.io/Experiments/"
description: "A running collection of self-contained studies in creative physics and generative geometry — each one a real implementation of a physical or mathematical system, in the browser."
---

### The Project

**Experiments** is the sketchbook I work in when I want to understand something
rather than ship something. Each entry is a self-contained study implementing a
genuine physical or geometric system in the browser — no libraries doing the
interesting part, no pre-rendered results.

![The Experiments index](featured.png)

The organising principle is that **implementation is a form of reading**. You can
follow a derivation of the Navier-Stokes equations on a manifold and feel that you
understand it; you find out whether you did when you have to decide what happens
at a cubemap seam. I publish them because the ambiguities are the valuable part
and they are invisible in a finished paper.

They are numbered and released in volumes, like a journal, which is only partly a
joke.

### Volume I — Published

- **№ 01 · Flame Fractals** — Iterated Function Systems after Scott Draves'
  fractal-flame algorithm. Nonlinear variations, logarithmic colour mapping,
  statistical super-sampling, up to 16 million GPU particles.
- **№ 02 · Gas Giant (S² FLIP)** — Fluid dynamics on a spherical manifold via a
  six-face cubemap atlas. Geodesic advection and a Jacobi pressure solve across
  the cube seams, with no pole singularity.
- **№ 03 · Solar Corona (MHD)** — Magnetohydrodynamics of the Sun's atmosphere:
  magnetic loop force fields, procedural coronal mass ejections, temperature-mapped
  colour.
- **№ 04 · Black Hole** — A ray-traced Schwarzschild black hole with gravitational
  lensing, Doppler boosting and accretion-disk dynamics, plus a WebGPU
  compute-based raymarch implementation.
- **№ 11 · Erosion** — True 3D volumetric weathering of layered desert rock. A 128³
  density field on RGBA16Float textures, rain and wind dissolution with
  angle-of-repose sediment transport, connectivity-based floater culling.
- **№ 12 · Audio Visualizer (STFT Spiral)** — A geometrically faithful mapping of
  the short-time Fourier transform into 3D: *x = f*, *y = |X|·cos ϕ*,
  *z = |X|·sin ϕ*. The phase every bar-graph analyser throws away, kept.
- **№ 13 · Arbor** — Space-colonisation tree growth with roots that steer around
  imported obstacle geometry, exporting textured USD/USDZ written in pure
  JavaScript.
- **№ 14 · Orogeny (S² Stream Power)** — Uplift, fluvial incision and deposition
  on a closed sphere. Equiangular cubed sphere with ghost-cell halos; the mass
  audit closes to **0.02% over 10,000 steps**, and built-in flatness, isotropy and
  mass tests verify it.

### Roadmap

**Volume II — Quantum & Chaos:** superfluid vortices (Ginzburg-Landau), N-body
galaxy formation (Barnes-Hut), 3D Schrödinger wave collapse with quantum
tunnelling, and high-precision strange attractors.

**Volume III — Morphogenesis:** Gray-Scott reaction-diffusion on arbitrary surface
meshes, and 3D diffusion-limited aggregation for mineral-like fractal growth.

### Technology

Vanilla JavaScript (ES6+), WebGL2 as primary with WebGPU where the compute demands
it, and GLSL shaders doing the parallelised physical integration. Typeset in
Cormorant Garamond and JetBrains Mono, because a laboratory notebook should look
like one.

Source is MIT; the generated imagery is CC BY-NC 4.0.

<div class="mt-8 mb-12">
    <a href="https://cyberhirsch.github.io/Experiments/" class="inline-flex items-center px-8 py-4 text-lg font-bold text-white transition-all bg-primary-600 rounded-lg hover:bg-primary-500 hover:scale-105 shadow-xl shadow-primary-900/20">
        Open the Laboratory &nbsp; &rarr;
    </a>
</div>

[View source on GitHub &rarr;](https://github.com/cyberhirsch/Experiments)
